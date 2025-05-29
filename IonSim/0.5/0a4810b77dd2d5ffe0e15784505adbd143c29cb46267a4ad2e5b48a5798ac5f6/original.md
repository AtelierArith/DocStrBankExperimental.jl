```
pointing!(laser::Laser, p::Vector{Tuple{T1, T2}} where T1<:Int where T2<:Real)
```

Sets the pointing of `laser` with `p`. `length(p)` should be equal to the number of ions in the `Chamber` containing `laser`.
