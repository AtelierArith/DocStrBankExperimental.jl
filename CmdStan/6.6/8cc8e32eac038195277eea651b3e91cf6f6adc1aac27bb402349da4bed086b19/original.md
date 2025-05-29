# Optimize type and constructor

Settings for Optimize top level method. 

### Method

```julia
Optimize(;
  method=Lbfgs(),
  iter=2000,
  save_iterations=false
)
```

### Optional arguments

```julia
* `method::OptimizeMethod`      : Optimization algorithm
* `iter::Int`                   : Total number of iterations
* `save_iterations::Bool`       : Stream optimization progress to output
```

### Related help

```julia
?Stanmodel                      : Create a StanModel
?OptimizeAlgorithm              : Available algorithms
```
