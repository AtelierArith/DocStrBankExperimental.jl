```
unsafe_load_state_vec(state_vec_pointer, num_elements)
```

Load a state vector from memory.

This function takes a pointer to a state vector and the number of elements in the vector.  It then loads the real and imaginary parts of the state vector from memory and returns a  complex array representing the state vector.

# Arguments

  * `state_vec_pointer`: A pointer to a state vector. This should be a struct with `real` and `imag` fields,  each of which is a pointer to a `Float64`.
  * `num_elements`: The number of elements in the state vector.

# Returns

  * A `Complex{Float64}` array representing the state vector.

# Warning

This function uses the `unsafe_load` function to directly load data from memory, which can be unsafe  if the pointers do not point to valid memory. Use with caution.
