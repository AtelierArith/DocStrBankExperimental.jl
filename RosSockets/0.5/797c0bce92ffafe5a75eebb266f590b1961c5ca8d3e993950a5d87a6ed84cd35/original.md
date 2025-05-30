```
receive_feedback_data(feedback_connection::FeedbackConnection, 
    timeout::Real = 10.0)
```

Waits for data to arrive from the ROS node and returns a struct of the data with the following fields: position, orientation, linear*vel, angular*vel. This function blocks execution while waiting, up to the timeout duration provided. If the timeout duration elapses without the arrival of data, throws a TimeoutError exception.

# Arguments

  * `feedback_connection`: the `FeedbackConnection` obtained from `open_feedback_connection`.
  * `timeout`: maximum time in seconds to wait for data.
