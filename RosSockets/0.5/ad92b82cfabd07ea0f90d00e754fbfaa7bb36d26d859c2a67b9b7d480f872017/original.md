```
send_receive(connection::Connection, msg::String, timeout::Real = 10.0)
```

Sends a message and waits for a response, which is then returned. This function blocks execution while waiting, up to the timeout duration provided. If the timeout duration elapses without the arrival of data, throws a TimeoutError exception. Note: the payload which is returned will be in a raw format. To convert to a string, use `String(payload)`. This string may further converted to other formats such as JSON.

# Arguments

  * `connection`: the `Connection` obtained from `open_connection`.
  * `msg`: the message to be sent. Note: some TCP servers may be require the   message be formatted a certain way (such as JSON), and may also require an   end of line character, such as `\n`, to terminate the message.
  * `timeout`: maximum time in seconds to wait for data.
