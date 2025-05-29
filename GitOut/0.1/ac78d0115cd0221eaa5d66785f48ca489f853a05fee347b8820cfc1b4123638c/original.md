```julia
git(args; post_args, kw...) -> Cmd

```

Create a `git` `Cmd` object as with [`git()`](@ref) but with additional arguments.  Arguments from the `post_args` argument are always applied after those from `arg`.  This is useful for other functions which don't provide access to `args` directly.  For example, `push(r; post_args=(tags=true,))` is equivalent to `push(r, tags=true)`.

Arguments can be passed either as an array or a key-value collection, the keys of which are the argument flag names.
