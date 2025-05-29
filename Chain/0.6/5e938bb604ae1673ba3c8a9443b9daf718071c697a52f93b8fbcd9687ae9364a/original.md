```
@chain(expr, exprs...)
```

Rewrites a series of expressions into a chain, where the result of one expression is inserted into the next expression following certain rules.

**Rule 1**

Any `expr` that is a `begin ... end` block is flattened. For example, these two pseudocodes are equivalent:

```julia
@chain a b c d e f

@chain a begin
    b
    c
    d
end e f
```

**Rule 2**

Any expression but the first (in the flattened representation) will have the preceding result inserted as its first argument, unless at least one underscore `_` is present. In that case, all underscores will be replaced with the preceding result.

If the expression is a symbol, the symbol is treated equivalently to a function call.

For example, the following code block

```julia
@chain begin
    x
    f()
    @g()
    h
    @i
    j(123, _)
    k(_, 123, _)
end
```

is equivalent to

```julia
begin
    local temp1 = f(x)
    local temp2 = @g(temp1)
    local temp3 = h(temp2)
    local temp4 = @i(temp3)
    local temp5 = j(123, temp4)
    local temp6 = k(temp5, 123, temp5)
end
```

**Rule 3**

An expression that begins with `@aside` does not pass its result on to the following expression. Instead, the result of the previous expression will be passed on. This is meant for inspecting the state of the chain. The expression within `@aside` will not get the previous result auto-inserted, you can use underscores to reference it.

```julia
@chain begin
    [1, 2, 3]
    filter(isodd, _)
    @aside @info "There are $(length(_)) elements after filtering"
    sum
end
```

**Rule 4**

It is allowed to start an expression with a variable assignment. In this case, the usual insertion rules apply to the right-hand side of that assignment. This can be used to store intermediate results.

```julia
@chain begin
    [1, 2, 3]
    filtered = filter(isodd, _)
    sum
end

filtered == [1, 3]
```

**Rule 5**

The `@.` macro may be used with a symbol to broadcast that function over the preceding result.

```julia
@chain begin
    [1, 2, 3]
    @. sqrt
end
```

is equivalent to

```julia
@chain begin
    [1, 2, 3]
    sqrt.(_)
end
```
