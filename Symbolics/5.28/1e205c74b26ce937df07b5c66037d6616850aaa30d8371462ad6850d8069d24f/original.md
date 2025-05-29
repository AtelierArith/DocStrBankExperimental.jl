```
@register_symbolic(expr, define_promotion = true, Ts = [Real])
```

Overload appropriate methods so that Symbolics can stop tracing into the registered function. If `define_promotion` is true, then a promotion method in the form of

```julia
SymbolicUtils.promote_symtype(::typeof(f_registered), args...) = Real # or the annotated return type
```

is defined for the register function. Note that when defining multiple register overloads for one function, all the rest of the registers must set `define_promotion` to `false` except for the first one, to avoid method overwriting.

# Examples

```julia
@register_symbolic foo(x, y)
@register_symbolic foo(x, y::Bool) false # do not overload a duplicate promotion rule
@register_symbolic goo(x, y::Int) # `y` is not overloaded to take symbolic objects
@register_symbolic hoo(x, y)::Int # `hoo` returns `Int`
```

See `@register_array_symbolic` to register functions which return arrays.
