Tail recursion that doesn't blow the stack.

```
@bounce even(n) = n == 0 ? true : odd(n-1)
@bounce odd(n) = n == 0 ? false : even(n-1)

even(1_000_000) # Blows up without `@bounce`.
#> true
```

For simple cases you probably want the much faster [`@rec`](@ref).
