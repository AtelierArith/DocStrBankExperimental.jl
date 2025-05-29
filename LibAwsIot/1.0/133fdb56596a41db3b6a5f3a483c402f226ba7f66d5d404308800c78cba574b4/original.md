```
aws_secure_tunnel_stop(secure_tunnel)
```

Asynchronous notify to the secure tunnel that you want it to transition to the stopped state. When the secure tunnel reaches the stopped state, all session state is erased.

# Arguments

  * `secure_tunnel`: secure tunnel to stop

# Returns

success/failure in the synchronous logic that kicks off the start process

### Prototype

```c
int aws_secure_tunnel_stop(struct aws_secure_tunnel *secure_tunnel);
```
