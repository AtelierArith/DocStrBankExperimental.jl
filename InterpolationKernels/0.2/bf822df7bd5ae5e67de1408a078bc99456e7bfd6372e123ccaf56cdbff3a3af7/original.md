```
CatmullRomSplinePrime{T}()
```

yields a kernel instance that is the 1st derivative of the Catmull-Rom interpolation kernel (see [`CatmullRomSpline`](@ref)) for floating-point type `T` which is assumed to be `Float64` if omitted.

The 1st derivative of the Catmull-Rom interpolation kernel is given by:

```
ker′(x) = ((9/2)*|x| - 5)*x                      if a = |x| ≤ 1
          (5 - (3/2)*|x|)*x - 4*sign(x)          if 1 ≤ |x| ≤ 2
          0                                      if |x| ≥ 2
```
