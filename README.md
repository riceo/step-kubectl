# kubectl

This step vendors the kubectl executable, and allows the user to execute a
command. Most options are passed along to the `kubectl` executable as is.

# Options:

- `debug` (optional, default: `false`) List the kubectl before running it.
Warning, all environment variables are expanded, including the password.
- `cmd` (optional) The kubectl command which needs to be run.
- `raw-global-args` (optional) Arguments that are placed before `cmd`.
- `raw-args` (optional) Arguments that are placed after `cmd`.

## Kubectl flags

The following options are available as wercker properties. The values are passed
directly to the `kubectl` command. See the `kubectl` for the documentation.

- `all`
- `current-replicas`
- `deployment-label-key`
- `file`
- `grace-period`
- `image`
- `insecure-skip-tls-verify`
- `interactive`
- `output`
- `overwrite`
- `password`
- `patch`
- `pod`
- `poll-interval`
- `replicas`
- `resource-version`
- `rollback`
- `selector`
- `server`
- `stdin`
- `template`
- `timeout`
- `token`
- `tty`
- `update-period`
- `username`

If a flag is not available, use the `raw-global-args` or the `raw-args` option.

# Example

```
deploy:
    steps:
      - kubectl:
          server: $KUBERNETES_MASTER
          username: $KUBERNETES_USERNAME
          password: $KUBERNETES_PASSWORD
          insecure-skip-tls-verify: true
          command: create -f cities-controller.json
```

# Google Container Engine (GKE) clusters

Passing a Google service account JSON keyfile as a string in optional parameter `gcloud-key-json` within your wercker.yml
will cause this script to use the gcloud cli utility to configure kubectl's access to GKE.

# License

The MIT License (MIT)

# Changelog

## 3.1.0

- Add support for authenticating kubectl with GKE clusters with a Google service account.

## 3.0.0

- Update to kubectl to version `1.3.4`

## 2.1.0

- Add `certificate-authority`, `client-certificate`, `client-key`

## 2.0.0

- Update to kubectl to version `1.2.0`

## 1.1.0

- Update to kubectl to version `1.1.3`

## 1.0.0

- Initial release
