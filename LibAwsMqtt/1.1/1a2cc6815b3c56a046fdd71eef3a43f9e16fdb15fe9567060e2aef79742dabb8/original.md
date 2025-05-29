Function that may transform the websocket handshake request. Called each time a websocket connection is attempted.

The default request uses path "/mqtt". All required headers are present, plus the optional header "Sec-WebSocket-Protocol: mqtt".

The user MUST invoke the `complete_fn` when transformation is complete or the application will soft-lock. When invoking the `complete_fn`, pass along the `request` and `complete_ctx` provided here and an error code. The error code should be AWS_ERROR_SUCCESS if transformation was successful, otherwise pass a different AWS_ERROR_X value.
