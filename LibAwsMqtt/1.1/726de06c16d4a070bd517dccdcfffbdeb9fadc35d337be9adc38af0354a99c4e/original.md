```
aws_mqtt_client_connection_set_login(connection, username, password)
```

Sets the username and/or password to send with the CONNECT packet.

# Arguments

  * `connection`:[in] The connection object
  * `username`:[in] The username to connect with
  * `password`:[in] [optional] The password to connect with

### Prototype

```c
int aws_mqtt_client_connection_set_login( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *username, const struct aws_byte_cursor *password);
```
