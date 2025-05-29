```
allrays(vrep::VRep)
```

V表現 `vrep` の中の光線と線に対するイテレータを返し、線を2つの光線に分割します。

### 例

```julia
vrep = Line([1, 0]) + Ray([0, 1])
collect(allrays(vrep)) # Returns [Ray([1, 0]), Ray([-1, 0]), Ray([0, 1])]
```
