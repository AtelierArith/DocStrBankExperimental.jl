```
CannonballFixedDrag(radius::Number, mass::Number, drag_coeff::Number)
```

Constructor for a fixed cannonball ballistic coefficient drag model.

The ballistic coefficient is computed with the following equation:

```
            BC = CD * area/mass
```

where area is the 2D projection of a sphere

```
            area = π * r^2
```

# Arguments

  * `radius::Number`: The radius of the spacecraft.
  * `mass::Number`: The mass of the spacecraft.
  * `drag_coeff::Number`: The drag coefficient of the spacecraft.

# Returns

  * `drag_model::CannonballFixedDrag`: A fixed ballistic coefficient drag model.
