```
sc_log(filename, lineno, package, category, priority, msg)
```

The central log function to be called by all packages. Dispatches the log calls by package and filters by category and priority.

### Parameters

  * `package`:[in] Must be a registered package id or -1.
  * `category`:[in] Must be `SC_LC_NORMAL` or `SC_LC_GLOBAL`.
  * `priority`:[in] Must be > `SC_LP_ALWAYS` and < `SC_LP_SILENT`.

### Prototype

```c
void sc_log (const char *filename, int lineno, int package, int category, int priority, const char *msg);
```
