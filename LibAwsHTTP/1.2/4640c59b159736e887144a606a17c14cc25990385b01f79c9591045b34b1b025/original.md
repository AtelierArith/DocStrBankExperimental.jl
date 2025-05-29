```
aws_websocket_on_connection_setup_data
```

Data passed to the websocket on_connection_setup callback.

An error_code of zero indicates that setup was completely successful. You own the websocket pointer now and must call [`aws_websocket_release`](@ref)() when you are done with it. You can inspect the response headers, if you're interested.

A non-zero error_code indicates that setup failed. The websocket pointer will be NULL. If the server sent a response, you can inspect its status-code, headers, and body, but this data will NULL if setup failed before a full response could be received. If you wish to persist data from the response make a deep copy. The response data becomes invalid once the callback completes.
