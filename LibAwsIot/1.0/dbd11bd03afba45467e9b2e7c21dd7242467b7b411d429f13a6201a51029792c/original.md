```
aws_secure_tunnel_state
```

The various states that the secure tunnel can be in. A secure tunnel has both a current state and a desired state. Desired state is only allowed to be one of {STOPPED, CONNECTED, TERMINATED}. The secure tunnel transitions states based on either (1) changes in desired state, or (2) external events.

Most states are interruptible (in the sense of a change in desired state causing an immediate change in state) but CONNECTING cannot be interrupted due to waiting for an asynchronous callback (that has no cancel) to complete.
