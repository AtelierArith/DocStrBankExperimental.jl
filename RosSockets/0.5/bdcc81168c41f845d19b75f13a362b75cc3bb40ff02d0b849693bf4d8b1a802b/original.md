```
send(connection::Connection, msg::String)
```

Send a message.

# Arguments

  * `connection`: the `Connection` obtained from `open_connection`.
  * `msg`: the message to be sent. Note: some TCP servers may be require the   message be formatted a certain way (such as JSON), and may also require an   end of line character, such as `\n`, to terminate the message.
