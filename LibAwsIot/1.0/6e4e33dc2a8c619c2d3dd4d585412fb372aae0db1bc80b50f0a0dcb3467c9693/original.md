```
aws_iotdevice_defender_config_set_task_period_ns(config, task_period_ns)
```

Sets the period of the device defender task

# Arguments

  * `config`:[in] defender task configuration
  * `task_period_ns`:[in] how much time in nanoseconds between defender task runs

# Returns

AWS_OP_SUCCESS when the property has been set properly. Returns an error code if the value was not able to be set.

### Prototype

```c
int aws_iotdevice_defender_config_set_task_period_ns( struct aws_iotdevice_defender_task_config *config, uint64_t task_period_ns);
```
