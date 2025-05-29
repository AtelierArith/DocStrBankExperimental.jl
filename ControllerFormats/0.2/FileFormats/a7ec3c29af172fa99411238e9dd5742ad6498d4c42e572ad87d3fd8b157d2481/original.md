```
read_MAT(filename::String; act_key::String)
```

Read a neural network stored in MATLAB's [`MAT`](https://www.mathworks.com/help/matlab/import_export/load-parts-of-variables-from-mat-files.html) format. This function requires to load the [`MAT.jl` library](https://github.com/JuliaIO/MAT.jl).

### Input

  * `filename` – name of the `MAT` file
  * `act_key`  – key used for the activation functions
  * `net_key`  – (optional; default: `nothing`) key used for the neural network

### Output

A [`FeedforwardNetwork`](@ref).

### Notes

The `MATLAB` file encodes a dictionary. If `net_key` is given, then the dictionary contains another dictionary under this key. Otherwise the outer dictionary directly contains the following:

  * A vector of weight matrices (under the name `"W"`)
  * A vector of bias vectors (under the name `"b"`)
  * A vector of strings for the activation functions (under the name passed via `act_key`)
