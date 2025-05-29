```
isplateau(i, x[, w=1; strict=true]) -> Union{Missing,Bool}
```

Test if `i` is a plateau in `x`, where a plateau is defined as a maxima or minima with consecutive equal (`==`) extreme values which are bounded by lesser values immediately before and after the consecutive values. Returns `false` if `i` is the last index in `x`.

See also: [`ismaxima`](@ref), [`isminima`](@ref)
