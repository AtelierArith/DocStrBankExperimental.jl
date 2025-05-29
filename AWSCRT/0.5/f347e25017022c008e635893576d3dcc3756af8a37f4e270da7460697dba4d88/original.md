```
ShadowClient(
    connection::MQTTConnection,
)
```

Device Shadow service client. [AWS Documentation](https://docs.aws.amazon.com/iot/latest/developerguide/iot-device-shadows.html).

Arguments:

  * `connection (MQTTConnection)`: MQTT connection to publish and subscribe on.
  * `thing_name (String)`: Name of the Thing in AWS IoT under which the shadow document will exist.
  * `shadow_name (Union{String,Nothing})`: Shadow name for a named shadow document or `nothing` for an unnamed shadow document.
