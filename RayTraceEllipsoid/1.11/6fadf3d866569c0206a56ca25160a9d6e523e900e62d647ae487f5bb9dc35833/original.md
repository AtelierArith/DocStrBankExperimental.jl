```
bend!(r::Ray, i::Interface)
```

Refract or reflect a ray with an interface. Update the direction of the ray. Returns if event failed, which is always `false` (see `raytrace!` for details why that is so).
