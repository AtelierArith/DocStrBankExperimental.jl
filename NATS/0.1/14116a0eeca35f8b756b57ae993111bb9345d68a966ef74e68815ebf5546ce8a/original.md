```julia
subscribe(
    connection,
    subject;
    queue_group,
    channel_size,
    monitoring_throttle_seconds
)

```

Subscribe to a subject in synchronous mode. Client is supposed to call `next` manually to obtain messages.

Optional keyword arguments are:

  * `queue_group`: NATS server will distribute messages across queue group members
  * `channel_size`: maximum items buffered for processing, if full messages will be ignored, default is `524288`, can be configured globally with `NATS_SUBSCRIPTION_CHANNEL_SIZE` env variable
  * `monitoring_throttle_seconds`: time intervals in seconds that handler errors will be reported in logs, default is `5.0` seconds, can be configured globally with `NATS_SUBSCRIPTION_ERROR_THROTTLING_SECONDS` env variable
