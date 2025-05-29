```
Grid::LaMEM_grid = read_LaMEM_inputfile(file, args::Union{String,Nothing}=nothing)
```

Parses a LaMEM input file and stores grid information in the `Grid` structure. Optionally, you can pass LaMEM command-line arguments as well.

# Example 1

```julia-repl
julia> Grid = read_LaMEM_inputfile("SaltModels.dat")
LaMEM Grid:
nel         : (32, 32, 32)
marker/cell : (3, 3, 3)
markers     : (96, 96, 96)
x           ϵ [-3.0 : 3.0]
y           ϵ [-2.0 : 2.0]
z           ϵ [-2.0 : 0.0]
```

# Example 2 (with command-line arguments)

```julia-repl
julia> Grid = read_LaMEM_inputfile("SaltModels.dat", args="-nel_x 64 -coord_x -4,4")
LaMEM Grid:
  nel         : (64, 32, 32)
  marker/cell : (3, 3, 3)
  markers     : (192, 96, 96)
  x           ϵ [-4.0 : 4.0]
  y           ϵ [-2.0 : 2.0]
  z           ϵ [-2.0 : 0.0]
```
