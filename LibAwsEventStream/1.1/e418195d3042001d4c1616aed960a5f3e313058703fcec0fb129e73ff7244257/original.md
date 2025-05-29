Invoked when a new stream has been received on the connection. If you return AWS_OP_SUCCESS (0), You must fill in the fields for continuation options or the program will assert and exit.

A failure path MUST leave the ref count of the continuation alone.

A success path should probably take a ref which will leave the continuation (assuming no other interference) at two AFTER creation is complete: 1 for the connection's continuation table, and one for the callback recipient which is presumably tracking it as well.
