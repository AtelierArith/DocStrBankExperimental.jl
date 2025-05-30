```
send_control_commands(robot_connection, controls)
```

ROSノードに制御コマンドのシーケンスを送信します。

# 引数

  * `robot_connection`: `open_robot_connection`から取得した`RobotConnection`。
  * `controls`: ベクトルのコレクション; 各ベクトルは線形速度と角速度のペアです。
