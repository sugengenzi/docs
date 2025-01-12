---
title: Secrets
layout: framework_docs
objective: Making credentials available to your production
order: 5
---

Running an application often involves a number of credentials, containing such things as database passwords, S3 buckets, and session encryption keys.

During development you will typically use [environment files](https://nodejs.org/dist/latest-v20.x/docs/api/cli.html#--env-fileconfig).  For security reasons, these files are generally excluded from being committed to version control or being deployed to production.

This means that you need another mechanism for setting up your production environment.  For fly.io, that mechanism is [secrets](https://fly.io/docs/reference/secrets/).

There are two ways to set secrets.  You can use the [fly secrets set](https://fly.io/docs/flyctl/secrets-set/) command:

```
fly secrets set SECRET_KEY=YOURSECRETKEYGOESHERE
```

Or you can import your dotenv file wholesale using [fly secrets import](https://fly.io/docs/flyctl/secrets-import/):

```
fly secrets import < .dotenv
```

Both commands will restart your application if it has previously been deployed.  Pass the `--stage` option if you would rather deploy these changes later.
