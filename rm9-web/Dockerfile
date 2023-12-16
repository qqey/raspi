FROM debian:bullseye

# GeoIPモジュールの有効化
RUN apt-get update && \
    apt-get install -y nginx=1.22.1-7 libnginx-mod-http-geoip

# GeoIPデータベースのダウンロード（例としてMaxMindのGeoIPデータベースを使用）
RUN mkdir -p /usr/share/GeoIP && \
    apt-get install -y curl && \
    curl -o /usr/share/GeoIP/GeoIP.dat.gz http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz && \
    gunzip /usr/share/GeoIP/GeoIP.dat.gz

# Nginx設定ファイルのコピー
COPY ./conf/nginx.conf /etc/nginx/nginx.conf

CMD ["nginx", "-g", "daemon off;"]
