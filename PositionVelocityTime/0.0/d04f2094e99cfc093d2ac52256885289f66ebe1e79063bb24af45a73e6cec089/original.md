Computes user position

```julia
user_position(prev_pos, rSats, ρ)
user_position(prev_pos, rSats, ρ, accuracy)

```

´rSats´: Array of Satellite positions. needs 3 values per satellite (xyz), size must be (3, N)") ´ρ´: Array of pseudo ranges 

Calculates the user position by least squares method. The algorithm is based on the common reception method. 
