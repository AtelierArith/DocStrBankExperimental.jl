```
set_step_increment!(lg, increment) -> Int
```

Sets the default increment applyed to logger `lg`'s iteration counter each time logging is performed.

Can be overidden by passing `log_step_increment=some_increment` when logging.
