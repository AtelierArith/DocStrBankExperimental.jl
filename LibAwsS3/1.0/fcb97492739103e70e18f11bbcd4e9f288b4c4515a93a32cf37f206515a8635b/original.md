```
aws_s3_init_default_signing_config(signing_config, region, credentials_provider)
```

Initialize the configuration for a default S3 signing.

### Prototype

```c
void aws_s3_init_default_signing_config( struct aws_signing_config_aws *signing_config, const struct aws_byte_cursor region, struct aws_credentials_provider *credentials_provider);
```
