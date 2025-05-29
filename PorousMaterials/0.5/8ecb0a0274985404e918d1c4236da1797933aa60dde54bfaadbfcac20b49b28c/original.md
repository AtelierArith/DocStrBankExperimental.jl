```
random_insertion!(molecules::Array{Molecule{Frac}, 1}, box::Box, template::Molecule{Cart})
```

Insert a molecule into the simulation box and perform a random rotation if needed. this function calls (`insert_w_random_orientation!`)[@ref], supplying it with a random position vector.

# Arguments

  * `molecules::Array{Molecule{Frac}, 1}`: array containing the molecules in the simulation
  * `box::Box`: the box  used for fractional coordinats
  * `template::Molecule{Cart}`: reference molecule of the type inserted
