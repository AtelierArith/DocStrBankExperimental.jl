```
LogEvent(message::AbstractString, datetime=Dates.now(tz"UTC"))
LogEvent(message::AbstractString, timestamp)
```

CloudWatch Logsへの送信用のログイベント。
