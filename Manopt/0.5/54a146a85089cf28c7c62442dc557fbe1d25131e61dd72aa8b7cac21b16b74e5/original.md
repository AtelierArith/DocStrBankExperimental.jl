```
DebugIfEntry <: DebugAction
```

Issue a warning, info, or error if a certain field does *not* pass a the `check`.

The `message` is printed in this case. If it contains a `@printf` argument identifier, that one is filled with the value of the `field`. That way you can print the value in this case as well.

# Fields

  * `io`:    an `IO` stream
  * `check`: a function that takes the value of the `field` as input and returns a boolean
  * `field`: symbol the entry can be accessed with within [`AbstractManoptSolverState`](@ref)
  * `msg`:   if the `check` fails, this message is displayed
  * `type`: symbol specifying the type of display, possible values `:print`, `: warn`, `:info`, `:error`,           where `:print` prints to `io`.

# Constructor

```
DebugEntry(field, check=(>(0)); type=:warn, message=":$f is nonnegative", io=stdout)
```
