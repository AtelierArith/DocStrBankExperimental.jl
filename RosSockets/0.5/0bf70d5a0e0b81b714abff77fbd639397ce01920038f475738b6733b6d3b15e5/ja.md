```
close_robot_connection(robot_connection; stop_robot=true)
```

ROSノードとの接続を閉じます。

# 引数

  * `robot_connection`: `open_robot_connection`から取得した`RobotConnection`。
  * `stop_robot`: シャットダウン前にロボットを停止するために、ROSノードにゼロ速度コマンドを発行します。
