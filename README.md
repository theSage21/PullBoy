PullBoy
=======

Pullboy is a VERY simple server that listens for incoming connections and deploys projects according to a predefined script.

Steps
-----

First we install pullboy. `pip install pullboy`. Second we write the deploy config file. An example would be:

```yaml
pullboy:
    workdir: '~/pullboy'
    script:
        - git pull origin master
        - make
    token: 'thisisnosecret'
```

Now we run pullboy with the following command `pullboy config.yaml`.

That's it.

To make pullboy deploy something all you need to do is hit the following URL.

`https://wherever.pullboy.is.running.com:8764/deploy` with the items `project` and `token` in the POST body. **HTTPS is recommended**.

Tokens are meant to be kept a secret otherwise anyone with access to this URL can deploy the code (we don't want it to be that simple do we?).

An example cURL command to deploy the project shown in the config above would be:

```bash
curl -X POST -F project=pullboy -F token=thisisnosecret https://wherever.pullboy.is.running.com:8764/deploy`
```
