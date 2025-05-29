```
allhalfspaces(hrep::HRep)
```

H-表現 `hrep` における半空間と超平面を反復するイテレータを返します。超平面は二つの半空間に分割されます。

### 例

```julia
hrep = HyperPlane([1, 0], 1) ∩ HalfSpace([0, 1], 1)
collect(allhalfspaces(hrep)) # Returns [HalfSpace([1, 0]), HalfSpace([-1, 0]), HalfSpace([0, 1])]
```
