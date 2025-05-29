```
Spider(narms::Int, armwidth::T, radius::T, origin::SVector{3,T} = SVector{3,T}(0.0, 0.0, 0.0), normal::SVector{3,T} = SVector{3,T}(0.0, 0.0, 1.0)) -> Vector{Rectangle{T}}
```

Creates a 'spider' obscuration with `narms` rectangular arms evenly spaced around a circle defined by `origin` and `normal`. Each arm is a rectangle `armwidth`×`radius`.

e.g. for 3 and 4 arms we get:

```
   |         _|_
  / \         |
```
