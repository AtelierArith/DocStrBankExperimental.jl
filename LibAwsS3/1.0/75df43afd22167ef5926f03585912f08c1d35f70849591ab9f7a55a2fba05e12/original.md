```
aws_s3express_credentials_provider_get_credentials(provider, original_credentials, properties, callback, user_data)
```

Async function for retrieving specific credentials based on properties.

callback will only be invoked if-and-only-if the return value was AWS_OP_SUCCESS.

# Arguments

  * `provider`: [`aws_s3express_credentials_provider`](@ref) provider to source from
  * `original_credentials`: The credentials used to derive the credentials for S3 Express.
  * `properties`: Specific properties for credentials being fetched.
  * `user_data`: user data to pass to the completion callback

### Prototype

```c
int aws_s3express_credentials_provider_get_credentials( struct aws_s3express_credentials_provider *provider, const struct aws_credentials *original_credentials, const struct aws_credentials_properties_s3express *properties, aws_on_get_credentials_callback_fn callback, void *user_data);
```
