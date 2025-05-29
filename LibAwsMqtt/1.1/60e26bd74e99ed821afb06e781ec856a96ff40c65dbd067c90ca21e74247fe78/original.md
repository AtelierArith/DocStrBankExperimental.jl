Function to invoke when the websocket handshake request transformation completes. This function MUST be invoked or the application will soft-lock.

`request` and `complete_ctx` must be the same pointers provided to the [`aws_mqtt_transform_websocket_handshake_fn`](@ref). `error_code` should should be AWS_ERROR_SUCCESS if transformation was successful, otherwise pass a different AWS_ERROR_X value.
