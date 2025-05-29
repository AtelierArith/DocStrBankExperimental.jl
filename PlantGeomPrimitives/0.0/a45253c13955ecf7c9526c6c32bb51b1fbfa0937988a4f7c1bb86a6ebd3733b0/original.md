```
Z()
```

Returns an unit vector in the direction of the Z axis as a `Vec` object. By default, the coordinates will be in double floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `Z(Float32)`.

```jldoctest
julia>  Z();

julia>  Z(Float32);
```
