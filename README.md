# Docker PHP-FPM & Nginx base on Alpine Linux

Lightweight docker image for CodeIgniter development

### Why should use this image

- Built on the lightweight and
  secure [Alpine Linux](https://www.alpinelinux.org/) distribution
- Multi-platform, supporting AMD4, ARMv6, ARMv7, ARM64
- Use [runit](http://smarden.org/runit/) instead
  of [supervisor](http://supervisord.org/)
- Tiny Docker image size

### PHP version supported

- [x] PHP 7.2
- [x] PHP 7.4
- [x] PHP 8.0
- [x] PHP 8.1 (recommend usage)
- [x] PHP 8.2 (recommend usage)
- [x] PHP 8.3
- [x] PHP 8.4

### How to use

- Build image

```shell
VERSION=7.2 make build # Build image with php 7.2
VERSION=7.4 make build # Build image with php 7.4
VERSION=8.0 make build # Build image with php 8.0
VERSION=8.1 make build # Build image with php 8.1
VERSION=8.2 make build # Build image with php 8.2
VERSION=8.3 make build # Build image with php 8.3
VERSION=8.4 make build # Build image with php 8.4
```

- How to customize image name

```shell
VERSION=7.2 IMAGE=yourname/codeigniter:php make build # Build image with php 7.2
```

- Test image by PHP version

```shell
VERSION=8.4 make test
VERSION=8.3 make test
VERSION=8.2 make test
VERSION=8.1 make test
VERSION=8.0 make test
VERSION=7.4 make test
VERSION=7.2 make test
```

- Test all images

```shell
make test-all
```

- Mount your code to be served with container

```shell
docker run --name=app -v /path/to/project:/var/www/html -p 80:80 pnlinh/codeigniter:php8.1
```

- Using docker-compose

```yaml
services:
  app:
    image: pnlinh/codeigniter:php8.1
    hostname: codeigniter-app
    container_name: codeigniter-app
    ports:
      - "80:80"
    volumes:
      - .:/var/www/html
    networks:
      - localnet
networks:
  localnet:
    driver: "bridge"
```

- Browser to: [http://localhost](http://localhost)

![image](https://github.com/pnlinh/docker-compose-template/assets/26193890/d26abb82-768c-49b7-b52a-7b5f03029a3c)

### Security scanner

- PHP 8.4

```terminaloutput
trivy image pnlinh/codeigniter:php8.4
2025-08-14T07:01:40+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:01:40+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:01:40+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:01:40+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:01:42+07:00	INFO	Detected OS	family="alpine" version="3.21.4"
2025-08-14T07:01:42+07:00	WARN	This OS version is not on the EOL list	family="alpine" version="3.21"
2025-08-14T07:01:42+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.21" repository="3.21" pkg_num=95
2025-08-14T07:01:42+07:00	INFO	Number of language-specific files	num=0

pnlinh/codeigniter:php8.4 (alpine 3.21.4)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

- PHP 8.3

```terminaloutput
trivy image pnlinh/codeigniter:php8.3
2025-08-14T07:00:53+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:00:53+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:00:53+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:00:53+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:00:56+07:00	INFO	Detected OS	family="alpine" version="3.20.7"
2025-08-14T07:00:56+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.20" repository="3.20" pkg_num=95
2025-08-14T07:00:56+07:00	INFO	Number of language-specific files	num=0

pnlinh/codeigniter:php8.3 (alpine 3.20.7)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

- PHP 8.2

```terminaloutput
trivy image pnlinh/codeigniter:php8.2
2025-08-14T07:02:14+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:02:14+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:02:14+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:02:14+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:02:17+07:00	INFO	Detected OS	family="alpine" version="3.20.7"
2025-08-14T07:02:17+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.20" repository="3.20" pkg_num=95
2025-08-14T07:02:17+07:00	INFO	Number of language-specific files	num=0

pnlinh/codeigniter:php8.2 (alpine 3.20.7)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

- PHP 8.1

```terminaloutput
trivy image pnlinh/codeigniter:php8.1
2025-08-14T07:02:37+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:02:37+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:02:37+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:02:37+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:02:39+07:00	INFO	Detected OS	family="alpine" version="3.19.8"
2025-08-14T07:02:39+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.19" repository="3.19" pkg_num=96
2025-08-14T07:02:39+07:00	INFO	Number of language-specific files	num=0

pnlinh/codeigniter:php8.1 (alpine 3.19.8)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

- PHP 7.4

```terminaloutput
trivy image pnlinh/codeigniter:php7.4
2025-08-14T07:03:04+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:03:04+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:03:04+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:03:04+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:03:07+07:00	INFO	Detected OS	family="alpine" version="3.15.11"
2025-08-14T07:03:07+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.15" repository="3.15" pkg_num=86
2025-08-14T07:03:07+07:00	INFO	Number of language-specific files	num=0
2025-08-14T07:03:07+07:00	WARN	This OS version is no longer supported by the distribution	family="alpine" version="3.15.11"
2025-08-14T07:03:07+07:00	WARN	The vulnerability detection may be insufficient because security updates are not provided

pnlinh/codeigniter:php7.4 (alpine 3.15.11)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

- PHP 7.2

```terminaloutput
trivy image pnlinh/codeigniter:php7.2
2025-08-14T07:03:27+07:00	INFO	[vuln] Vulnerability scanning is enabled
2025-08-14T07:03:27+07:00	INFO	[secret] Secret scanning is enabled
2025-08-14T07:03:27+07:00	INFO	[secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2025-08-14T07:03:27+07:00	INFO	[secret] Please see also https://aquasecurity.github.io/trivy/v0.58/docs/scanner/secret#recommendation for faster secret detection
2025-08-14T07:03:29+07:00	INFO	Detected OS	family="alpine" version="3.8.5"
2025-08-14T07:03:29+07:00	INFO	[alpine] Detecting vulnerabilities...	os_version="3.8" repository="3.8" pkg_num=79
2025-08-14T07:03:29+07:00	INFO	Number of language-specific files	num=0
2025-08-14T07:03:29+07:00	WARN	This OS version is no longer supported by the distribution	family="alpine" version="3.8.5"
2025-08-14T07:03:29+07:00	WARN	The vulnerability detection may be insufficient because security updates are not provided

pnlinh/codeigniter:php7.2 (alpine 3.8.5)

Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

### Add Xdebug

- See [docs/xdebug-support.md](docs/xdebug-support.md)

### Add SSL in local

- See [docs/enable-https.md](docs/enable-https.md)

### References

- [TrafeX/docker-php-nginx](https://github.com/TrafeX/docker-php-nginx)
- [Runit vs Supervisor](https://bolshov.online/docker/2020/11/18/runit-vs-supervisor)
- [Add trusted root CA to Alpine](https://stackoverflow.com/questions/67231714/how-to-add-trusted-root-ca-to-docker-alpine/67232164#67232164)
