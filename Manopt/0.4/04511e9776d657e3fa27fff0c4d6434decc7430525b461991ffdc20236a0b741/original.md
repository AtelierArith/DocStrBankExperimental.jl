```
DebugIterate <: DebugAction
```

debug for the current iterate (stored in `get_iterate(o)`).

# Constructor

```
DebugIterate()
```

# Parameters

  * `io`:        (`stdout`) default stream to print the debug to.
  * `format`:    (`"$prefix %s"`) format how to print the current iterate
  * `long`:      (`false`) whether to have a long (`"current iterate:"`) or a short (`"p:"`) prefix
  * `prefix`     (see `long` for default) set a prefix to be printed before the iterate
