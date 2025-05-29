```
tropics_extratropics(A::ClimArray; lower_lat=30, higher_lat=90) → tropics, extratropics
```

与えられた配列を2つの配列に分けます：1つは緯度 ℓ ∈ [-lower*lat, +lower*lat] を持ち、もう1つは [-higher*lat:-lower*lat, lower*lat:higher*lat] を持ちます。
