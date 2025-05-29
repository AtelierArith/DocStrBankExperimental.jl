```
billiard_sinai(r=0.25, x=1.0, y=1.0; setting = "standard")
```

Return a vector of obstacles that defines a Sinai billiard of size (`x`, `y`) with a disk in its center, of radius `r`.

In the periodic case, the system is also known as "Lorentz Gas".

### Settings

  * "standard" : Specular reflection occurs during collision.
  * "periodic" : The walls are `PeriodicWall` type, enforcing periodicity at the boundaries
  * "random" : The velocity is randomized upon collision.
  * "ray-splitting" : All obstacles in the billiard allow for ray-splitting.
