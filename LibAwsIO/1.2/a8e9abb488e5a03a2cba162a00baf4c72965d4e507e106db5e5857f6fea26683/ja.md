```
aws_pipe_subscribe_to_readable_events(read_end, on_readable, user_data)
```

パイプが読み取り可能になる（エッジトリガー）か、エラーが発生したときに通知を受け取るために購読します。`on_readable`は、パイプに読み取るデータがある場合や、パイプにエラーがある場合にイベントループのスレッドで呼び出されます。`on_readable`は、ユーザーがすべてのデータを読み取った後に再度呼び出され、その後に新しいデータが到着した場合に呼び出されます。新しいデータが到着したときにパイプにまだ未読のデータがある場合は、再度呼び出されないことに注意してください。これは、接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_subscribe_to_readable_events( struct aws_pipe_read_end *read_end, aws_pipe_on_readable_fn *on_readable, void *user_data);
```
