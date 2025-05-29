```
set_K!(pid::DiscretePID, K, r, y)
```

Update `K` in the PID controller. This function takes the current reference and measurement as well in order to provide bumpless transfer. This is realized by updating the internal state `I`.

Note: Due to the bumpless transfer, setting $K = 0$ does not imply that the controller output will be 0 if the integral state is non zero. To reset the controller state, call `reset_state!(pid)`.
