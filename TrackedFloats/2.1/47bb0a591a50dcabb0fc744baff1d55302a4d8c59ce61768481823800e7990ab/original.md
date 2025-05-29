```
tf_init()
```

Initialize the global TrackedFloats configuration. (Automatically called when using function by `__init__`)

We need to make this a function, otherwise it can cache the value of the timestamp used for writing unique log files.
