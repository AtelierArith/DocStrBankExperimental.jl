Invoked upon completion of the TLS handshake. If successful error_code will be AWS_OP_SUCCESS, otherwise the negotiation failed and immediately after this function is invoked, the channel will be shutting down.

NOTE: When using SecItem the handler and slot arguments will be pointers to the socket slot and socket handler. This is due to TLS negotiaion being handled by the Apple Network Framework connection in the socket slot/handler.
