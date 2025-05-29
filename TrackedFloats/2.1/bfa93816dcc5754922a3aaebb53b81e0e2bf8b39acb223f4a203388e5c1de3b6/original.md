```
tf_exclude_stacktrace(exclusions = [:prop])
```

Globally set the types of stack traces to not collect.

See documentation for the `event()` function for details on the types of events that can be put into this list.

Convenience function; You can also set the stack trace exclusions with a keyword argument to `tf_config_logger`.
