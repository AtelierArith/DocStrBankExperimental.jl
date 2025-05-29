Protocol that abstracts a [Mosquitto.jl](https://github.com/denglerchr/Mosquitto.jl) client for Mango agents.

# Creation

```
MQTTProtocol(client_id::String, broker_addr::InetAddr)
```

Create an MQTT client that connects to the broker at `broker_addr` with a `client_id`.

# Fields

  * client - Mosquitto.jl client
  * broker_addr - address of the MQTT broker to connect to
  * connected - internal flag indicating connection status
  * active - internal flag indicating listen loop activity
  * msg_channel - message channel of the MQTT client
  * conn_channel - connection channel of the MQTT client
  * topic*to*aid - internal dictionary to track which registered agent is subscribed to which topic
