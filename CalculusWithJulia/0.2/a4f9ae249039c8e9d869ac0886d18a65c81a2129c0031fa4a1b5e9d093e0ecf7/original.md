```
lim(f, c; n=6, m=1, dir="+-")
lim(f, c, dir; n-5)
```

Means to generate numeric table of values of `f` as `h` gets close to `c`.

  * `n`, `m`: powers of `10` to add (subtract) to (from) `c`.
  * `dir`: Either `"+-"` (show left and right), `"+"` (right limit), or `"-"` (left limit). Can also use functions `+`, `-`, `±`.

Example:

```
julia> f(x) = sin(x) / x
f (generic function with 1 method)

julia> lim(f, 0)
 0.1        0.9983341664682815
 0.01       0.9999833334166665
 0.001      0.9999998333333416
 0.0001     0.9999999983333334
 1.0e-5     0.9999999999833332
 1.0e-6     0.9999999999998334
   ⋮          ⋮
   c          L?
   ⋮          ⋮
-1.0e-6     0.9999999999998334
-1.0e-5     0.9999999999833332
-0.0001     0.9999999983333334
-0.001      0.9999998333333416
-0.01       0.9999833334166665
-0.1        0.9983341664682815
```
