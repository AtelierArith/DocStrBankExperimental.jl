```
onbounds(loc::T, bounds::Bounds{T}) where T<:Union{LLA,ENU}
```

Check whether a location `loc` is onbounds `bounds` Works only for points that have passed the inbounds test
