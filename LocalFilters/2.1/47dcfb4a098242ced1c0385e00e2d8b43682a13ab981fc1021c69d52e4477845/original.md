```
LocalFilters.ball(Dims{N}, r)
```

yields a mask approximating a `N`-dimensional ball of radius `r`. The result is `N`-dimensional array of Boolean's with all dimensions odd and equal and whose values are `true` inside the ball (where distance to the center `≤ r`) and `false` otherwise. The mask may be used to specify the neighborhood, the kernel, or the structuring element in local filtering operations.

The returned mask has centered axes, to get a mask with 1-based indices, call:

```
LocalFilters.ball(Dims{N}, r).parent
```

See also [`LocalFilters.kernel`](@ref) and [`LocalFilters.strel`](@ref).
