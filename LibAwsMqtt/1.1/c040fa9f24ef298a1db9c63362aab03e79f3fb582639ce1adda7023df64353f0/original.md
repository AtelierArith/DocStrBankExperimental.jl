```
aws_mqtt_client_new(allocator, bootstrap)
```

Creates an instance of [`aws_mqtt_client`](@ref).

# Arguments

  * `allocator`:[in] The allocator the client will use for all future allocations
  * `bootstrap`:[in] The client bootstrap to use to initiate new socket connections

# Returns

a new instance of an [`aws_mqtt_client`](@ref) if successful, NULL otherwise

### Prototype

```c
struct aws_mqtt_client *aws_mqtt_client_new(struct aws_allocator *allocator, struct aws_client_bootstrap *bootstrap);
```
