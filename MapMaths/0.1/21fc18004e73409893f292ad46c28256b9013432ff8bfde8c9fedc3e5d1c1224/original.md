```
tdist(a,b) -> Number
```

Compute the "tunnel distance" between points `a` and `b`.

Tunnel distance is the straight-line distance in Euclidean space, i.e. `norm(ECEF(a) - ECEF(b))`.

Each of `a` and `b` may be any of the following:

  * A pair of north-south and east-west coordinates.
  * A two-dimensional coordinate.
  * Either of the above with an additional altitude.

# Example

```jldoctest
julia> tdist(EastNorth(0,0), EastNorth(3,4))
5.0000000000001075

julia> tdist(EastNorth(0,0), (EastNorth(3,0), Alt(4)))
5.0000005648476336

julia> tdist(EastNorth(0,0), (East(3), North(0), Alt(4)))
5.0000005648476336
```
