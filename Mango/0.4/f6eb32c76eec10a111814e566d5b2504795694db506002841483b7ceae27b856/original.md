```
send_message(
container::ContainerInterface,
content::Any,
address::Address,
sender_id::Union{Nothing,String}=nothing;
kwargs...,
```

)

Send a message `message` using the given container `container` to the given address. Additionally, further keyword arguments can be defines to fill the internal meta data of the message.
