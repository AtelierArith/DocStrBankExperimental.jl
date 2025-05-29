```
billiard_rectangle(x=1.0, y=1.0; setting = "standard")
```

Return a vector of obstacles that defines a rectangle billiard of size (`x`, `y`).

### Settings

  * "standard" : Specular reflection occurs during collision.
  * "periodic" : The walls are `PeriodicWall` type, enforcing periodicity at the boundaries
  * "random" : The velocity is randomized upon collision.
  * "ray-splitting" : All obstacles in the billiard allow for ray-splitting.
