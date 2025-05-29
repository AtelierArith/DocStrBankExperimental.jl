```
designMatrix(setting)

Return matrix of independent variables including the variable (ones) of the constanst term for a given regression setting.
```

# Arguments

  * `setting::RegressionSetting`: A regression setting object.

# Notes

```
Design matrix is a matrix which holds values of independent variables on its columns for a given linear regression model.
```

# Examples

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> designMatrix(setting)
24×2 Matrix{Float64}:
 1.0  50.0
 1.0  51.0
 1.0  52.0
 1.0  53.0
 1.0  54.0
 1.0  55.0
 1.0  56.0
 1.0  57.0
 1.0  58.0
 1.0  59.0
 1.0  60.0
 1.0  61.0
 1.0  62.0
 1.0  63.0
 1.0  64.0
 1.0  65.0
 1.0  66.0
 1.0  67.0
 1.0  68.0
 1.0  69.0
 1.0  70.0
 1.0  71.0
 1.0  72.0
 1.0  73.0
```
