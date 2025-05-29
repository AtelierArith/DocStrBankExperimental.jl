```
CannonballFixedSRP(radius::Number, mass::Number, drag_coeff::Number)
```

Constructor for a fixed cannonball ballistic coefficient SRP model.

The ballistic coefficient is computed with the following equation:

```
            RC = CD * area/mass
```

where area is the 2D projection of a sphere

```
            area = π * r^2
```

# Arguments

  * `radius::Number`: The radius of the spacecraft.
  * `mass::Number`: The mass of the spacecraft.
  * `reflectivity_coeff::Number`: The reflectivity coefficient of the spacecraft.

# Returns

  * srp_model::CannonballFixedSRP`: A fixed ballistic coefficient SRP model.
