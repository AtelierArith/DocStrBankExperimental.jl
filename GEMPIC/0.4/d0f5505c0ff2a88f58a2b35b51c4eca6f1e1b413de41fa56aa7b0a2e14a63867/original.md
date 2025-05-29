```
add_charge_pp!(ρ_dofs, pm, xp, yp, wp)
```

## Add charge of single particle

  * Information about the 2d mesh

      * delta_x(2)  : Value of grid spacing along both directions.
      * domain(2,2) : Definition of the domain: domain(1,1) = x1*min, domain(2,1) = x2*min,  domain(1,2) = x1*max, domain(2,2) = x2*max
  * Information about the particles

      * no_particles : Number of particles of underlying PIC method (processor local)
      * n_span : Number of intervals where spline non zero (degree + 1)
      * scaling
  * position : Particle position
  * wp : Particle weight times charge
  * ρ_dofs : spline coefficient of accumulated density
