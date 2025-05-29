```
DebugEntryChange{T} <: DebugAction
```

print a certain entries change during iterates

# Additional fields

  * `print`:    (`print`) function to print the result
  * `prefix`:   (`"Change of :Iterate"`) prefix to the print out
  * `format`:   (`"$prefix %e"`) format to print (uses the `prefix by default and scientific notation)
  * `field`:    Symbol the field can be accessed with within [`AbstractManoptSolverState`](@ref)
  * `distance`: function (p,o,x1,x2) to compute the change/distance between two values of the entry
  * `storage`:  a [`StoreStateAction`](@ref) to store the previous value of `:f`

# Constructors

```
DebugEntryChange(f,d)
```

# Keyword arguments

  * `io`:             (`stdout`) an `IOStream`
  * `prefix`:         (`"Change of $f"`)
  * `storage`:        (`StoreStateAction((f,))`) a [`StoreStateAction`](@ref)
  * `initial_value`: an initial value for the change of `o.field`.
  * `format`:         (`"$prefix %e"`) format to print the change
