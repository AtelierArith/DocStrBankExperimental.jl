```
wait_for_ready_state(client::WSClient; retry_delay::Real = 0.3,
    timeout::Real = 10)
```

Wait for the document ready state to be complete. Throws a TimeoutError if the timeout is reached.
