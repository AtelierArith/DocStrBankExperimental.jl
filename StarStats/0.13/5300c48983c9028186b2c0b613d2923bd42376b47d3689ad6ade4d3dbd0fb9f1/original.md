```
ModelDataGrid
```

Struct containing the definition of a grid including the input variables defining it and their values 

# Fields:

  * dfs: Multidimensional array of DataFrames containing individual evolutionary track information from a grid of models.       This is populated with the load_grid function.
  * inputs: Vector of String vectors containing the parth of the path from a track. (TODO give an example)
  * input_names: Vector of Symbol containing the names of each parameter of the grid.
  * input_values: Result of parsing the inputs into floats.
  * EEPs: Array of integers representing the Equivelant Evolutionary Points (see Dotter, 2016)
  * Xc_TAMS: Float denoting the limit  in central hydrogen at which one defines the TAMS
