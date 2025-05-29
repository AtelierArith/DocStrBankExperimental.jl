```julia
person_parameter(M, responses, betas, alg; init, kwargs...)

```

Estimate a single person parameter for an item response theory model `M` from a response vector (`responses`) given item parameters `beta` and an estimation algorithm `alg`.

## Examples

### 1 Parameter Logistic Model

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> responses = [0, 1, 1, 0, 0];

julia> betas = [0.2, -1.3, 0.4, 1.2, 0.0];

julia> person_parameter(OnePL, responses, betas, MLE())
PersonParameter{Float64}(-0.34640709530672537, 0.9812365857368596)
```

### 3 Parameter Logistic Model

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> responses = [0, 1, 1];

julia> betas = [(a = 1.0, b = 0.3, c = 0.1), (a = 0.3, b = -0.5, c = 0.0), (a = 1.4, b = 1.1, c = 0.3)];

julia> person_parameter(ThreePL, responses, betas, WLE())
PersonParameter{Float64}(0.657715606325967, 1.5321777539977457)
```
