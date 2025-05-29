```
aws_iotdevice_defender_config_register_number_list_metric(task_config, metric_name, supplier, userdata)
```

Adds number list custom metric to the Device Defender task configuration. Has no impact on a defender task already started using the configuration.

# Arguments

  * `task_config`:[in] the defender task configuration to register the metric to
  * `metric_name`:[in] UTF8 byte string of the metric name
  * `supplier`:[in] callback function to produce the metric value when requested at report generation time
  * `userdata`:[in] specific callback data for the supplier callback function

### Prototype

```c
void aws_iotdevice_defender_config_register_number_list_metric( struct aws_iotdevice_defender_task_config *task_config, const struct aws_byte_cursor *metric_name, aws_iotdevice_defender_get_number_list_fn *supplier, void *userdata);
```
