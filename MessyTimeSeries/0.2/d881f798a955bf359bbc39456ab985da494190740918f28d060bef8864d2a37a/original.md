```
isconverged(new::Float64, old::Float64, tol::Float64, ε::Float64, increasing::Bool)
```

Check whether `new` is close enough to `old`.

# Arguments

  * `new`: new objective or loss
  * `old`: old objective or loss
  * `tol`: tolerance
  * `ε`: small Float64
  * `increasing`: true if `new` increases, at each iteration, with respect to `old`
