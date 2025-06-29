```
CloudWatchLogHandler(
    config::AWSConfig,
    log_group_name,
    log_stream_name,
    formatter::Memento.Formatter,
)
```

Construct a Memento Handler for logging to a CloudWatch Log Stream. This constructor creates a task which asynchronously submits logs to the stream.

A CloudWatch Log Event has only two properties: `timestamp` and `message`.

If a `Record` has a `date` property it will be used as the `timestamp`, otherwise the current time will be captured when `Memento.emit` is called. All `DateTime`s will be assumed to be in UTC.

The `message` will be generated by calling `Memento.format` on the `Record` with this handler's `formatter`.
