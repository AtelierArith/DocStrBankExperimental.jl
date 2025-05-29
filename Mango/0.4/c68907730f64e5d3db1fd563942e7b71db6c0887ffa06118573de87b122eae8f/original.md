```
forward_to(agent, content, forward_to_address, received_meta; kwargs...)
```

Forward the message to a specific agent using the metadata received on handling the message. This method essentially simply calls send_message on the input given, but also adds and fills the correct metadata fields to mark the message as forwarded. 

For this the following meta data is set.

  * 'forwarded=true',
  * 'forwarded*from*address=address of the original sender',
  * 'forwarded*from*id=id of the original sender'
