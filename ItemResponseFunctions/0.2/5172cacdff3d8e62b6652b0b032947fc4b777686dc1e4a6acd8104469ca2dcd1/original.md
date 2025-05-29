```julia
information(M, theta, betas; scoring_function)

```

Calculate the test information of an item response mode `M` at the ability value `theta` given a vector of item parameters `betas`. The values of betas are considered item parameters for different items.

The test information is calculated from the models [`iif`](@ref) function. For details on how to pass item parameters to [`iif`](@ref), see the respective function documentation.

## Examples

### 1 Parameter Logistic Model

```jldoctest
julia> information(OnePL, 0.0, zeros(6))
1.5

julia> betas = fill((; b = 0.0), 6);

julia> information(OnePL, 0.0, betas)
1.5
```

### 2 Parameter Logistic Model

```jldoctest
julia> betas = fill((; a = 1.2, b = 0.4), 4);

julia> information(TwoPL, 0.0, betas)
1.3601401228069936
```

### 3 Parameter Logistic Model

```jldoctest
julia> betas = fill((; a = 1.5, b = 0.5, c = 0.2), 4);

julia> information(ThreePL, 0.0, betas)
1.1021806599852655
```

### 4 Parameter Logistic Model

```jldoctest
julia> betas = fill((; a = 0.5, b = 1.4, c = 0.13, d = 0.94), 6);

julia> information(FourPL, 0.0, betas)
0.20178122985757524
```
