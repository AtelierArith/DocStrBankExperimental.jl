```
aws_iotdevice_defender_config_create(config_out, allocator, thing_name, report_format)
```

Creates a new reporting task config for Device Defender metrics collection

# Arguments

  * `config_out`:[in] output to write a pointer to a task configuration. Will write non-NULL if successful in creating the the task configuration. Will write NULL if there is an error during creation
  * `allocator`:[in] allocator to use for the task configuration's internal data, and the task itself when started
  * `thing_name`:[in] thing name the task config is reporting for
  * `report_format`:[in] report format to produce when publishing to IoT

# Returns

AWS_OP_SUCCESS and config_out will be non-NULL. Returns an error code otherwise

### Prototype

```c
int aws_iotdevice_defender_config_create( struct aws_iotdevice_defender_task_config **config_out, struct aws_allocator *allocator, const struct aws_byte_cursor *thing_name, enum aws_iotdevice_defender_report_format report_format);
```
