```
receive_feedback_data(feedback_connection::FeedbackConnection, 
    timeout::Real = 10.0)
```

ROSノードからデータが到着するのを待ち、次のフィールドを持つデータの構造体を返します: position, orientation, linear*vel, angular*vel。この関数は、指定されたタイムアウト期間まで待機中に実行をブロックします。タイムアウト期間が経過してもデータが到着しない場合、TimeoutError例外をスローします。

# 引数

  * `feedback_connection`: `open_feedback_connection`から取得した`FeedbackConnection`。
  * `timeout`: データを待つ最大時間（秒単位）。
