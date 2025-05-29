```
xkb_context_set_log_fn(context, log_fn)
```

Set a custom function to handle logging messages.

By default, log messages from this library are printed to stderr. This function allows you to replace the default behavior with a custom handler. The handler is only called with messages which match the current logging level and verbosity settings for the context. level is the logging level of the message. *format* and *args* are the same as in the vprintf(3) function.

You may use [`xkb_context_set_user_data`](@ref)() on the context, and then call [`xkb_context_get_user_data`](@ref)() from within the logging function to provide it with additional private context.

xkb_context

### Parameters

  * `context`: The context in which to use the set logging function.
  * `log_fn`: The function that will be called for logging messages. Passing NULL restores the default function, which logs to stderr.
