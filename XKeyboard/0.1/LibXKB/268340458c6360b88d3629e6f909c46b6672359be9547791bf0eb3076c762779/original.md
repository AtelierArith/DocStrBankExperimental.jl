```
xkb_context_set_log_level(context, level)
```

Set the current logging level.

The default level is XKB_LOG_LEVEL_ERROR. The environment variable XKB_LOG_LEVEL, if set in the time the context was created, overrides the default value. It may be specified as a level number or name.

xkb_context

### Parameters

  * `context`: The context in which to set the logging level.
  * `level`: The logging level to use. Only messages from this level and below will be logged.
