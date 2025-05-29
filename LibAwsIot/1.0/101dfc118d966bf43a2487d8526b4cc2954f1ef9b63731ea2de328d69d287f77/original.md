```
aws_iotdevice_defender_config_set_report_rejected_fn(config, rejected_fn)
```

Sets the report rejected callback function to invoke when is canceled and not going to be scheduled to run. This is a suggestion of when it is OK to close or free resources kept around while the task is running.

# Arguments

  * `config`:[in] defender task configuration
  * `rejected_fn`:[in] rejected report callback function

# Returns

AWS_OP_SUCCESS when the report rejected callback has been set. Returns an error if the callback was not set

### Prototype

```c
int aws_iotdevice_defender_config_set_report_rejected_fn( struct aws_iotdevice_defender_task_config *config, aws_iotdevice_defender_report_rejected_fn *rejected_fn);
```
