```
@unsafe
```

A workaround for an upstream bug on Ubuntu 24. It disables sandboxing in Electron.  Run this macro before calling `gogui()`.

The recommended way of using PackageMaker on Ubuntu 24 is however to use from VSCode, as  in this case it works OK without calling `@unsafe`

# Examples

```julia-repl
julia> @unsafe;
julia> gogui()
```
