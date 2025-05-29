```
@unpack_option [should_throw=false] options unpack_expr
```

Unpacks a value from `options` depending on the form of `unpack_expr`. 

If `unpack_expr` is of the form `name`, with `name::Symbol`, then this macro is  equivalent to writing 

```julia
$name = options[$name]
```

If `should_throw == true`, throws an `ArgumentError` if `options` does not contain key `$name`.

Otherwise, returns an `ArgumentError` from the current function if `options` does not contain key `$name`.

If `unpack_expr` is of the form 

  * `name::T`, then `options[$name]` must be of type `T` or an `ArgumentError` will be *returned*
  * `name::Union{T1, T2, ..., Tn}`, then `options[$name]` must be of type `T1, T2, ...,` or `Tn`
  * `name = default`, then `default_value` will be used if `$name` is not present in `options`
  * `name => new_name`, is the equivalent to `$new_name = options[$name]`

An `unpack_expr` of the form `(name => new_name)::T`, `name::T = default` or `name::Union{T1, T2, ..., Tn} = default`, etc., also behaves as expected.
