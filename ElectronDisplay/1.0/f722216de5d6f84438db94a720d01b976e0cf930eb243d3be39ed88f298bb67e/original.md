```
electrondisplay([mime,] x; config...)
```

Show `x` in Electron window.  Use MIME `mime` if specified.  The keyword arguments can be used to override [`ElectronDisplay.CONFIG`](@ref) without mutating it.

# Examples

```julia
electrondisplay(@doc reduce; single_window=true, focus=false)
```
