```
aws_iotdevice_defender_config_set_task_failure_fn(config, failure_fn)
```

Sets the task failure callback function to invoke when the running of the task encounters a failure. Though this is optional to specify, it is important to register a handler to at least monitor failure that stops the task from running

The most likely scenario for task not being able to continue is failure to reschedule the task

# Arguments

  * `config`:[in] defender task configuration
  * `failure_fn`:[in] failure callback function

# Returns

AWS_OP_SUCCESS when the task failure callback has been set. Returns an error if the callback was not set

### Prototype

```c
int aws_iotdevice_defender_config_set_task_failure_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_task_failure_fn *failure_fn);
```
