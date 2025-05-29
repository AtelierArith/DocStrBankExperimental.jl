```julia
@indirect function interface_function end
```

Declare an `interface_function` in the upstream module (i.e., the module "owning" the function `interface_function`).  This function can be used and/or extended in downstream packages (via `@indirect import Module`) without loading the package defining `interface_function`. This from of `@indirect` works only at the top-level module.

```julia
@indirect function interface_function(...) ... end
```

Define a method of `interface_function` in the upstream module.  The function `interface_function` must be declared first by the above syntax.

This can also be used in downstream modules provided that `interface_function` is imported by `@indirect import Module: interface_function` (see below).

```julia
@indirect import Module
```

Import an upstream module `Module` indirectly.  This defines a constant named `Module` which acts like the module in a limited way. Namely, `Module.f` can be used to extend or call function `f`, provided that `f` in the actual module `Module` is declared to be an "indirect function" (see above).

```julia
@indirect import Module: f1, f2, ..., fn
```

Import "indirect functions" `f1`, `f2`, ..., `fn`.  This defines constants `f1`, `f2`, ..., and `fn` that are extendable (see above) and callable.

```julia
@indirect function Module.interface_function(...) ... end
```

Define a method of an indirectly imported function.  This form can be usable only in downstream modules where `Module` is imported via `@indirect import Module`.

# Examples

Suppose you want extend functions in `Upstream` package in `Downstream` package without importing it.

## Step 1: Declare indirect functions in the Upstream package

There must be a package that "declares" the ownership of an indirect function. Typically, such function is an interface extended by downstream packages.

To declare a function `fun` in a package `Upstream` wrap an empty definition of a function `function fun end` with `@indirect`:

```julia
module Upstream
    using IndirectImports
    @indirect function fun end
end
```

To define a method of an indirect function inside `Upstream`, wrap it in `@indirect`:

```julia
module Upstream
    using IndirectImports
    @indirect function fun end

    @indirect fun() = 0  # defining a method
end
```

## Step 2: Add the upstream package in the Downstream package

Use Pkg.jl interface as usual to add `Upstream` package as a dependency of the `Downstream` package; i.e., type `]add Upstream⏎`:

```julia-repl
(Downstream) pkg> add Upstream
```

This puts the entry `Upstream` in `[deps]` of `Project.toml`:

```toml
[deps]
...
Upstream = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
...
```

If it is not ideal to install `Upstream` by default, move it to `[extras]` section (you may need to create it manually):

```toml
[extras]
Upstream = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

## Step 3: Add method definitions in the Downstream package

Once `Upstream` is registered in `Project.toml`, you can import `Upstream` and define its functions, provided that they are prefixed with `@indirect` macro:

```julia
module Downstream
    using IndirectImports
    @indirect import Upstream
    @indirect Upstream.fun(x) = x + 1
    @indirect function Upstream.fun(x, y)
        return x + y
    end
end
```

**Note**: It looks like defining a method works without `@indirect` possibly due to a "bug" in Julia [^1].  While it is handy to define methods without `@indirect` for debugging, prototyping, etc., it is a good idea to wrap the method definition in `@indirect` to be forward compatible with future Julia versions.

[^1]: Extending a constructor is possible with only using `using`   [https://github.com/JuliaLang/julia/issues/25744](https://github.com/JuliaLang/julia/issues/25744)

# Limitation

Function declarations can be documented as usual

```julia
"""
Docstring for `fun`.
"""
@indirect function fun end
```

but it does not work with the method definitions:

```julia
# Commenting out the following errors:

# """
# Docstring for `fun`.
# """
@indirect function fun()
end
```

To add a docstring to indirect functions in downstream packages, one workaround is to use "off-site" docstring:

```julia
@indirect function fun() ... end

"""
Docstring for `fun`.
"""
fun
```

# How it works

See [https://discourse.julialang.org/t/23526/38](https://discourse.julialang.org/t/23526/38) for a simple self-contained code to understanding the idea.  Note that the actual implementation is slightly different.
