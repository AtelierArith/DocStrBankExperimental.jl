```
send_control_commands(robot_connection, controls)
```

Send a sequence of control commands to the ROS node.

# Arguments

  * `robot_connection`: the `RobotConnection` obtained from `open_robot_connection`.
  * `controls`: a collection of vectors; each vector is a pair of linear and angular velocities.
