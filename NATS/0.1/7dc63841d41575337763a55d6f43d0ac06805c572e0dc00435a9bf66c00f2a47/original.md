```julia
subscribe(
    f,
    connection,
    subject;
    queue_group,
    spawn,
    channel_size,
    monitoring_throttle_seconds
)

```

Subscribe to a subject.

Optional keyword arguments are:

  * `queue_group`: NATS server will distribute messages across queue group members
  * `spawn`: if `true` task will be spawn for each `f` invocation, otherwise messages are processed sequentially, default is `false`
  * `channel_size`: maximum items buffered for processing, if full messages will be ignored, default is `524288`, can be configured globally with `NATS_SUBSCRIPTION_CHANNEL_SIZE` env variable
  * `monitoring_throttle_seconds`: time intervals in seconds that handler errors will be reported in logs, default is `5.0` seconds, can be configured globally with `NATS_SUBSCRIPTION_ERROR_THROTTLING_SECONDS` env variable
