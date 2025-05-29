```
submit_logs(stream::CloudWatchLogStream, events::AbstractVector{LogEvent}) -> Int
```

Submit a list of log events to AWS.

None of the log events can be more than 2 hours in the future, or older than 14 days or the retention period of the log group. If this occurs, those log messages will be rejected but the rest will succeed.

Submission of *all* log events will fail if:

  * the log events are more than 1 MiB of data
  * the log events are not in chronological order by timestamp
  * there are more than 10000 log events in `events`
  * the log events span more than 24 hours

Returns the number of events successfully submitted.
