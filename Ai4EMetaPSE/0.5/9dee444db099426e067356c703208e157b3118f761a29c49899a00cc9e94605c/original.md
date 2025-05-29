```julia
generatecode(
    io::AbstractString,
    type::Ai4EMetaPSE.jsonModel;
    write2File
) -> Ai4EMetaPSE.MetaSolution

```

To read the json file and return [`MetaSolution`](@ref) type

  * `io`: Json file name or json strings
  * `type`: The type of json, `CommonJson` , `ModelJson` and so on.
  * `write2File`: The name of script to be generated or nothing. If passing nothing, it will not generate script. `Default`: nothing

# Examples:

```julia
str = """{
    "name": "Name",
    "pkgs": [
        "ModelingToolkit",
        "DifferentialEquations"
    ],
    "variables": [
        "x(t) = 1.0",
        "y(t) = 1.0",
        "z(t) = 2.0"
    ],
    "parameters": [
        "σ = 1.0",
        "ρ = 3.0",
        "β = 5.0" 
    ],
    "equations": [
        "der(x) = σ*(y - x)",
        "der(y) = x*(ρ - z) - y",
        "der(z) = x*y - β*z"
    ],
    "u0": [
        "x => 1.0",
        "y => 2.0",
        "z => 3.0"
    ],
    "timespan": [0,1,0.1],
    "solver": "Rosenbrock23"
}"""
solution = generatecode(str, CommonJson(); write2File="s.jl")
```
