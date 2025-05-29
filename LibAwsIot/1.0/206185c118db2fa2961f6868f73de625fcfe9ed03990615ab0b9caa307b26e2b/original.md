```
aws_iotdevice_defender_config_set_callback_userdata(config, userdata)
```

Sets the userdata for the device defender task's callback functions

# Arguments

  * `config`:[in] defender task configuration
  * `userdata`:[in] how much time in nanoseconds between defender task runs

# Returns

AWS_OP_SUCCESS when the property has been set properly. Returns an error code if the value was not able to be set

### Prototype

```c
int aws_iotdevice_defender_config_set_callback_userdata( struct aws_iotdevice_defender_task_config *config, void *userdata);
```
