```
close_robot_connection(robot_connection; stop_robot=true)
```

Close the connection with the ROS node.

# Arguments

  * `robot_connection`: the `RobotConnection` obtained from `open_robot_connection`.
  * `stop_robot`: issues a zero-velocity command to the ROS node to stop the robot before shutdown.
