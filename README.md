# Develop plugin or theme with Docker Compose

It provides WordPress, MariaDB, WP-CLI suite for WordPress development.

## Set up

1. Clone or fork this repo.

2. Put your plugin or theme code in the root of this folder and adjust the 
   `services/wordpress/volumes` section of `docker-compose.yml` so that it
   syncs to the appropriate directory.

3. Add `mywp.test` to `/etc/hosts`, e.g.:

   ```
   127.0.0.1 mywp.test
   ```

## Start environment

```sh
docker-compose up -d
```

The first time you run this, it will take a few minutes to pull in the required
images. On subsequent runs, it should take less than 30 seconds before you can
connect to WordPress in your browser. (Most of this time is waiting for MariaDB
to be ready to accept connections.)

The `-d` flag backgrounds the process and log output. To view logs for a
specific container, use `docker-compose logs [container]`, e.g.:

```sh
docker-compose logs wordpress
```

Open `http://mywp.test/` and follow the steps to install WordPress.

Alternatively, you can navigate to `http://mywp.test/` and manually perform
the famous five-second install.


## WP-CLI

You will probably want to [create a shell alias][3] for this:

```sh
docker-compose run --rm wp-cli wp [command]
```
