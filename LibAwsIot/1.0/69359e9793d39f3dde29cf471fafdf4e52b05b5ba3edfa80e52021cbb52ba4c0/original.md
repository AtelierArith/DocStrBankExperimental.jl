```
aws_secure_tunnel_start(secure_tunnel)
```

Asynchronous notify to the secure tunnel that you want it to attempt to connect. The secure tunnel will attempt to stay connected.

# Arguments

  * `secure_tunnel`: secure tunnel to start

# Returns

success/failure in the synchronous logic that kicks off the start process

### Prototype

```c
int aws_secure_tunnel_start(struct aws_secure_tunnel *secure_tunnel);
```
