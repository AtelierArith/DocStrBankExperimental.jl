```
billiard_bunimovich(l=1.0, w=1.0)
```

Return a vector of `Obstacle`s that define a Buminovich billiard, also called a stadium. The length is considered *without* the attached semicircles, meaning that the full length of the billiard is `l + w`. The left and right edges of the stadium are [`Semicircle`](@ref)s.

`billiard_stadium` is an alias of `billiard_bunimovich`.
