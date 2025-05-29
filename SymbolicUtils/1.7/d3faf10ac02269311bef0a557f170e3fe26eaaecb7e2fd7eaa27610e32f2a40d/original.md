similarterm(x, head, args, symtype=nothing; metadata=nothing, exprhead=:call)

Returns a term that is in the same closure of types as `typeof(x)`, with `head` as the head and `args` as the arguments, `type` as the symtype and `metadata` as the metadata. By default this will execute `head(args...)`. `x` parameter can also be a `Type`. The `exprhead` keyword argument is useful  when manipulating `Expr`s.
