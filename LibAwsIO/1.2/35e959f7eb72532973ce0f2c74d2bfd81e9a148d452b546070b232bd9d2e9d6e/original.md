Generic event function for channel lifecycle events.

Callbacks are provided for: (1) Channel creation (2) Channel setup - If TLS is being used, this function is called once the socket has connected, the channel has been initialized, and TLS has been successfully negotiated. A TLS handler has already been added to the channel. If TLS negotiation fails, this function will be called with the corresponding error code. If TLS is not being used, this function is called once the socket has connected and the channel has been initialized. (3) Channel shutdown

These callbacks are always invoked within the thread of the event-loop that the channel is assigned to.

This function does NOT always imply "success" – if error_code is AWS_OP_SUCCESS then everything was successful, otherwise an error condition occurred.
