```julia
drain(connection, sub; timer)

```

Unsubscribe a subscription and wait for precessing all messages in the buffer.

Underneeth it periodicaly checks for state of the buffer, interval for checks is configurable per connection with `drain_poll` parameter of `connect` method. It can also be set globally with `NATS_DRAIN_POLL_INTERVAL_SECONDS` environment variable. If not set explicitly default polling interval is `0.2` seconds. 

Optional keyword arguments:

  * `timer`: error will be thrown if drain not finished until `timer` expires. Default value is configurable per connection on `connect` with `drain_timeout`. Can be also set globally with `NATS_DRAIN_TIMEOUT_SECONDS` environment variable. If not set explicitly default drain timeout is `5.0` seconds.
