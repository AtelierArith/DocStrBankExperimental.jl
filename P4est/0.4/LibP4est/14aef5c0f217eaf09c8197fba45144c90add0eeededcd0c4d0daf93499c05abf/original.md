```
sc_set_log_defaults(log_stream, log_handler, log_thresold)
```

Controls the default SC log behavior.

### Parameters

  * `log_stream`:[in] Set stream to use by `sc_logf` (or NULL for stdout).
  * `log_handler`:[in] Set default SC log handler (NULL selects builtin).
  * `log_threshold`:[in] Set default SC log threshold (or `SC_LP_DEFAULT`). May be `SC_LP_ALWAYS` or `SC_LP_SILENT`.

### Prototype

```c
void sc_set_log_defaults (FILE * log_stream, sc_log_handler_t log_handler, int log_thresold);
```
