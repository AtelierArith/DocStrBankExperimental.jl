```
C = griddata(A::ClimGrid, B::ClimGrid; min=[], max=[])
```

Interpolate `ClimGrid` A onto the lon-lat grid of `ClimGrid` B, where A and B are `ClimGrid`.

Min and max optional keyword are used to constraint the results of the interpolation. For example, interpolating bounded fields can lead to unrealilstic values, such as negative precipitation. In that case, one would use min=0.0 to convert negative precipitation to 0.0.
