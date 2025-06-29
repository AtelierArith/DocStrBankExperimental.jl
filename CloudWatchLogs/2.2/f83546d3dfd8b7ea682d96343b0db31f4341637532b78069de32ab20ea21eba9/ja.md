```
submit_logs(stream::CloudWatchLogStream, events::AbstractVector{LogEvent}) -> Int
```

AWSにログイベントのリストを送信します。

ログイベントのいずれも、未来に2時間以上、または14日以上前、またはロググループの保持期間を超えてはなりません。これが発生した場合、それらのログメッセージは拒否されますが、残りは成功します。

*すべての*ログイベントの送信は、以下の場合に失敗します：

  * ログイベントのデータが1 MiBを超えている
  * ログイベントがタイムスタンプによって時系列順でない
  * `events`にログイベントが10000を超えている
  * ログイベントが24時間を超えている

成功裏に送信されたイベントの数を返します。
