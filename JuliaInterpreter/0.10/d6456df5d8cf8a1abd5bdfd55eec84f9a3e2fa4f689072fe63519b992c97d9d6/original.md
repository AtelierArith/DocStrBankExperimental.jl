```
on_breakpoints_updated(f)
```

Register a two-argument function to be called after any update to the set of all breakpoints. This includes their creation, deletion, enabling and disabling.

The function `f` should take two inputs:

  * First argument is the function doing to update, this is provided to allow to dispatch on its type. It will be one:

      * `::typeof(breakpoint)` for the creation,
      * `::typeof(remove)` for the deletion.
      * `::typeof(update_states)` for disable/enable/toggleing
  * Second argument is the breakpoint object that was changed.

If only desiring to handle some kinds of update, `f` should have fallback methods to do nothing in the general case.

!!! warning
    This feature is experimental, and may be modified or removed in a minor release.

