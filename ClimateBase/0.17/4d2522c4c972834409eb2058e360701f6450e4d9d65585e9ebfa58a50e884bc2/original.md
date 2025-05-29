```
tropics_extratropics(A::ClimArray; lower_lat=30, higher_lat=90) → tropics, extratropics
```

Separate the given array into two arrays: one having latitudes ℓ ∈ [-lower*lat, +lower*lat], and one having [-higher*lat:-lower*lat, lower*lat:higher*lat].
