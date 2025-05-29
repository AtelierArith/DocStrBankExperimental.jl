```julia
person_parameters(M, responses, betas, alg)

```

Estimate person parameters for an item response theory model of type `M` given item parameters `betas`, an estimation algorithm `alg` and `responses` for each person.

`responses` can be a vector of responses where each entry corresponds to the responses for a person, or a response matrix with `size(responses) == (n, length(betas))`, i.e. each row of the response matrix corresponds to the responses of a single person.

## Examples

### 1 Parameter Logistic Model

```jldoctest
julia> responses = [1 1 0; 0 1 0; 1 1 0; 0 0 1]
4×3 Matrix{Int64}:
 1  1  0
 0  1  0
 1  1  0
 0  0  1

julia> betas = [-0.1, 0.0, 1.0];

julia> person_parameters(OnePL, responses, betas, MLE());
```
