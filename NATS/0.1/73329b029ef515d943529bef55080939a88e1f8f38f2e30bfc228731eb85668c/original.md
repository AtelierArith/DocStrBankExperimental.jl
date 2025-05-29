```julia
drain(connection)

```

Unsubscribe all subscriptions, wait for precessing all messages in buffers, then close connection. Drained connection is no more usable. This method is used to gracefuly stop the process.

Underneeth it periodicaly checks for state of all buffers, interval for checks is configurable per connection with `drain_poll` parameter of `connect` method. It can also be set globally with `NATS_DRAIN_POLL_INTERVAL_SECONDS` environment variable. If not set explicitly default polling interval is `0.2` seconds.

Error will be written to log if drain not finished until timeout expires. Default timeout value is configurable per connection on `connect` with `drain_timeout`. Can be also set globally with `NATS_DRAIN_TIMEOUT_SECONDS` environment variable. If not set explicitly default drain timeout is `5.0` seconds.
