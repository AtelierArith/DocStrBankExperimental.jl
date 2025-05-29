```
aws_iotdevice_defender_config_set_task_cancelation_fn(config, cancel_fn)
```

Sets the task cancelation callback function to invoke when the task is canceled and not going to be scheduled to run. This is a suggestion of when it is OK to close or free resources kept around while the task is running.

# Arguments

  * `config`:[in] defender task configuration
  * `cancel_fn`:[in] cancelation callback function

# Returns

AWS_OP_SUCCESS when the task cancelation callback has been set. Returns an error if the callback was not set

### Prototype

```c
int aws_iotdevice_defender_config_set_task_cancelation_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_task_canceled_fn *cancel_fn);
```
