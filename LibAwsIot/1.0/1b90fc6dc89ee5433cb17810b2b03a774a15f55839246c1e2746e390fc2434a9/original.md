```
aws_iotdevice_defender_task_create(task_out, config, connection, event_loop)
```

Creates and starts a new Device Defender reporting task

# Arguments

  * `task_out`:[out] output parameter to set to point to the defender task
  * `config`:[in] defender task configuration to use to start the task
  * `connection`:[in] mqtt connection to use to publish reports to
  * `event_loop`:[in] IoT device thing name used to determine the MQTT topic to publish the report to and listen for accepted or rejected responses

# Returns

AWS_OP_SUCCESS if the task has been created successfully and is scheduled to run

### Prototype

```c
int aws_iotdevice_defender_task_create( struct aws_iotdevice_defender_task **task_out, const struct aws_iotdevice_defender_task_config *config, struct aws_mqtt_client_connection *connection, struct aws_event_loop *event_loop);
```
