Function that may accept or reject a websocket handshake response. Called each time a valid websocket connection is established.

All required headers have been checked already (ex: "Sec-Websocket-Accept"),

Return AWS_OP_SUCCESS to accept the connection or AWS_OP_ERR to stop the connection attempt.
