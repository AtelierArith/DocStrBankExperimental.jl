```
resubscribe_existing_topics(connection::MQTTConnection)
```

現在のすべてのトピックに再度サブスクライブします。これは、クリーンセッションで接続を再開する際に役立ちます。

タスクとSUBSCRIBEパケットのIDを返します。タスクは、サーバーからSUBACKが受信されると完了します。

成功した場合、タスクには以下のメンバーを持つ辞書が含まれます：

  * `:packet_id (Int)`: 確認されているSUBSCRIBEパケットのID。
  * `:topics (Vector{Tuple{Union{String,Nothing},aws_mqtt_qos}})`: 確認されているSUBSCRIBEパケットのトピックフィルターとそのQoSレベル。トピックは、トピックの再サブスクライブに失敗した場合は`nothing`になります。再サブスクライブするトピックがない場合、ベクターは空になります。

失敗した場合、タスクには例外が含まれます。

SUBSCRIBEパケットを送信できなかった場合は例外をスローします。
