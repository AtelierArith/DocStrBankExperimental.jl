The factory function for S3 client to create a S3 Express credentials provider. The S3 client will be the only owner of the S3 Express credentials provider.

During S3 client destruction, S3 client will start the destruction of the provider, and wait the on_provider_shutdown_callback to be invoked before the S3 client finish destruction.

Note to implement the factory properly: - Make sure `on_provider_shutdown_callback` will be invoked after the provider finish shutdown, otherwise, leak will happen. - The provider must not acquire a reference to the client; otherwise, a circular reference will cause a deadlock. - The `client` provided CANNOT be used within the factory function call or the destructor.

# Arguments

  * `allocator`: memory allocator to create the provider.
  * `client`: The S3 client uses and owns the provider.
  * `on_provider_shutdown_callback`: The callback to be invoked when the provider finishes shutdown.
  * `shutdown_user_data`: The user data to invoke shutdown callback with
  * `user_data`: The user data with the factory

# Returns

The [`aws_s3express_credentials_provider`](@ref).
