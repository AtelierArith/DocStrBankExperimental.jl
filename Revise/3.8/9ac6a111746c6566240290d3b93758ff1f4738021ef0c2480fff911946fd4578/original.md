```
includet(filename::AbstractString)
```

Load `filename` and track future changes. `includet` is intended for quick "user scripts"; larger or more established projects are encouraged to put the code in one or more packages loaded with `using` or `import` instead of using `includet`. See https://timholy.github.io/Revise.jl/stable/cookbook/ for tips about setting up the package workflow.

By default, `includet` only tracks modifications to *methods*, not *data*. See the extended help for details. Note that this differs from packages, which evaluate all changes by default. This default behavior can be overridden; see [Configuring the revise mode](@ref).

# Extended help

## Behavior and justification for the default revision mode (`:evalmeth`)

`includet` uses a default `__revise_mode__ = :evalmeth`. The consequence is that if you change

```
a = [1]
f() = 1
```

to

```
a = [2]
f() = 2
```

then Revise will update `f` but not `a`.

This is the default choice for `includet` because such files typically mix method definitions and data-handling. Data often has many untracked dependencies; later in the same file you might `push!(a, 22)`, but Revise cannot determine whether you wish it to re-run that line after redefining `a`. Consequently, the safest default choice is to leave the user in charge of data.

## Workflow tips

If you have a series of computations that you want to run when you redefine your methods, consider separating your method definitions from your computations:

  * method definitions go in a package, or a file that you `includet` *once*
  * the computations go in a separate file, that you re-`include` (no "t" at the end) each time you want to rerun your computations.

This can be automated using [`entr`](@ref).

## Internals

`includet` is essentially shorthand for

```
Revise.track(Main, filename; mode=:includet, skip_include=true)
```

Do *not* use `includet` for packages, as those should be handled by `using` or `import`. If `using` and `import` aren't working, you may have packages in a non-standard location; try fixing it with something like `push!(LOAD_PATH, "/path/to/my/private/repos")`. (If you're working with code in Base or one of Julia's standard libraries, use `Revise.track(mod)` instead, where `mod` is the module.)

`includet` is deliberately non-recursive, so if `filename` loads any other files, they will not be automatically tracked. (Call [`Revise.track`](@ref) manually on each file, if you've already `included`d all the code you need.)
