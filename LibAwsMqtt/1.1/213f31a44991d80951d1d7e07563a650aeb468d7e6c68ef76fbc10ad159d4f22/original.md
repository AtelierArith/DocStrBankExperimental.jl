Called when a publish message is received.

# Arguments

  * `connection`:[in] The connection object
  * `topic`:[in] The information channel to which the payload data was published.
  * `payload`:[in] The payload data.
  * `dup`:[in] DUP flag. If true, this might be re-delivery of an earlier attempt to send the message.
  * `qos`:[in] Quality of Service used to deliver the message.
  * `retain`:[in] Retain flag. If true, the message was sent as a result of a new subscription being made by the client.
