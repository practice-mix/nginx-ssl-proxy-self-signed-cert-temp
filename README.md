

```shell
openssl req  -subj '//CN=localhost.org'  -addext "subjectAltName = DNS:localhost.org"  -x509 -sha256 -nodes -days 10000 -newkey rsa:2048 -keyout self.key -out self.crt

```
notice: 
- windows git bash use //CN，linux use /CN
- windows install self.crt

---
if dup container, then 
```shell
docker stop nginx-proxy && docker container rm  nginx-proxy
```
---

refresh nginx.conf
```shell
docker exec -it nginx-proxy nginx -s reload
```

# issues
## x509: certificate signed by unknown authority
install self.crt, restart docker vm 

# reference
https://leangaurav.medium.com/simplest-https-setup-nginx-reverse-proxy-letsencrypt-ssl-certificate-aws-cloud-docker-4b74569b3c61
https://medium.com/@oliver.zampieri/self-signed-ssl-reverse-proxy-with-docker-dbfc78c05b41
