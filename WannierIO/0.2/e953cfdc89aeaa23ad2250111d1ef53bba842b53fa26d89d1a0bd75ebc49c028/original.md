```
read_win(filename; fix_inputs=true)
read_win(filename, ::Wannier90Text; fix_inputs=true)
read_win(filename, ::Wannier90Toml; fix_inputs=true)
```

Read wannier90 input `win` file.

# Arguments

  * `filename`: The name of the input file.

# Keyword Arguments

  * `fix_inputs`: sanity check and fix the input parameters, e.g., set   `num_bands = num_wann` if `num_bands` is not specified,   convert `atoms_cart` always to `atoms_frac`, etc.   See also [`fix_win!`](@ref).
