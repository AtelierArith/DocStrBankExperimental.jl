```
deepcopy(px)
```

Make a new parcellation containing a `deepcopy` of all parcels from `px`. Note however that, as with `deepcopy(p::Parcel)`, the surface remains just a reference and is not  itself copied, since it may be a large object.
