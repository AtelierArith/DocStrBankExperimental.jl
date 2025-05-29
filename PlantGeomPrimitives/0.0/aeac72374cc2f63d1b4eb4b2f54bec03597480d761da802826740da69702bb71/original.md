```
O()
```

Returns the origin of the 3D coordinate system as a `Vec` object. By default, the coordinates will be in double floating precision (`Float64`) but it is possible to generate a version with lower floating precision as in `O(Float32)`.

```jldoctest
julia>  O();

julia>  O(Float32);
```
