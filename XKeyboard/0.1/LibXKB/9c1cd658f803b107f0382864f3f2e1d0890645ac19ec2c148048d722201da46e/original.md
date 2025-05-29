```
xkb_context_set_log_verbosity(context, verbosity)
```

Sets the current logging verbosity.

The library can generate a number of warnings which are not helpful to ordinary users of the library. The verbosity may be increased if more information is desired (e.g. when developing a new keymap).

The default verbosity is 0. The environment variable XKB_LOG_VERBOSITY, if set in the time the context was created, overrides the default value.

Most verbose messages are of level XKB_LOG_LEVEL_WARNING or lower.

xkb_context

### Parameters

  * `context`: The context in which to use the set verbosity.
  * `verbosity`: The verbosity to use. Currently used values are 1 to 10, higher values being more verbose. 0 would result in no verbose messages being logged.
