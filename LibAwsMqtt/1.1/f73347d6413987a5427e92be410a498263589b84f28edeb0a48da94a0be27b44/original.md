```
aws_mqtt5_negotiated_settings_copy(source, dest)
```

Makes an owning copy of a negotiated settings structure.

Used in downstream.

# Arguments

  * `source`: settings to copy from
  * `dest`: settings to copy into. Must be in a zeroed or initialized state because it gets clean up called on it as the first step of the copy process.

# Returns

success/failure

### Prototype

```c
int aws_mqtt5_negotiated_settings_copy( const struct aws_mqtt5_negotiated_settings *source, struct aws_mqtt5_negotiated_settings *dest);
```
