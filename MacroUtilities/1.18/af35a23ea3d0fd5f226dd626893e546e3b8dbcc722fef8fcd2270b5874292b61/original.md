```
@parse_kwargs [args] kwarg_spec
```

Parses the set of keyword expressions given in `args` according to a series of `kwarg_spec` specification and sets the corresponding keys in the calling scope. Returns a `Vector` of the expressions that were not parsed as keyword arguments.

`kwarg_spec` must be a block `Expr`, with each line consisting of an expression of the form 

```julia
    key = (expected_type = T)
```

which specifies that for a key-value expression in `args` of the form `key = value`, `value` must have type `T`.

An alternative form is 

```julia
    key = (expected_types = (T1, T2, ..., Tn))
```

which specifies that a key-value expression in `args` with `key = value` must have `typeof(value) in (T1, T2, ..., Tn)`

If the `default` key is provided, e.g., 

```julia
    key = (expected_types = (T1, T2, ..., Tn), default=default_value)
```

then `key` is set to `default_value` if `args` do not contain a `key = value` expression. 

If the `default` key is not provided, then args must contain a `key = value` expression or an `ArgumentError` will be thrown. 

An alternative, more compact, form to the above expressions is

```julia
    key::Union{T1, T2, ..., Tn} = default_value
```

Note: If `key::Symbol` is provided as part of `kwarg_spec`, the expression `key` in `args` is treated as `key=key)` (i.e., akin to the usual kwarg syntax `f(; key)`). 

# Examples

```jldoctest
julia> macro a(args...)
       @parse_kwargs args... begin
           a1::Union{Int, Symbol, Expr}
           a2::Union{String, Nothing}
           a3::Bool = false
       end
       quote
        b1 = $a1
        b2 = $a2
        b3 = $a3
        (; b1, b2, b3)
       end |> esc
       end
@a (macro with 1 method)

julia> let 
           a1 = 1
           @a a1 a2="b2"
       end
(b1 = 1, b2 = "b2", b3 = false)

julia> let 
           @a a2="b2"
       end
ERROR: LoadError: ArgumentError: No value provided for key `a1`
[...]
```
