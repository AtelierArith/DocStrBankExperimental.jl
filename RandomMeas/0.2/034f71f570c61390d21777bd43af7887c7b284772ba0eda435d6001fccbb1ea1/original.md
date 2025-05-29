```
multiply(shadow1::AbstractShadow, shadow2::AbstractShadow)
```

Multiply two shadow objects of the same concrete type.

# Arguments:

  * `shadow1::AbstractShadow`: The first shadow object.
  * `shadow2::AbstractShadow`: The second shadow object.

# Returns

A new shadow object representing the product.

# Throws

An `ArgumentError` if the types of `shadow1` and `shadow2` do not match.

# Example

```julia
prod_shadow = multiply(shadow1, shadow2)
```
