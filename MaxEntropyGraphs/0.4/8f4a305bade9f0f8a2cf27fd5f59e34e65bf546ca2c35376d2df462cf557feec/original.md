```
L_DBCM_reduced(θ::Vector, k_out::Vector, k_in::Vector, F::Vector, nz_out::Vector, nz_in::Vector, n::Int=length(k_out))
```

Compute the log-likelihood of the reduced DBCM model using the exponential formulation in order to maintain convexity.

# Arguments

```
- `θ`: the maximum likelihood parameters of the model ([α; β])
- `k_out`: the reduced outdegree sequence
- `k_in`: the reduced indegree sequence
- `F`: the frequency of each pair in the degree sequence
- `nz_out`: the indices of non-zero elements in the reduced outdegree sequence
- `nz_in`: the indices of non-zero elements in the reduced indegree sequence
- `n`: the number of nodes in the reduced model
```

The function returns the log-likelihood of the reduced model. For the optimisation, this function will be used to generate an anonymous function associated with a specific model.

# Examples

```jldoctest
# Generic use:
julia> k_out  = [1, 1, 1, 2, 2, 2, 3, 3, 4, 4, 4, 5, 5];

julia> k_in   = [2, 3, 4, 1, 3, 5, 2, 4, 1, 2, 4, 0, 4];

julia> F      = [2, 2, 1, 1, 1, 2, 3, 1, 1, 2, 2, 1, 1];

julia> θ      = collect(range(0.1, step=0.1, length=length(k_out)));

julia> nz_out = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

julia> nz_in  = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 13];

julia> n      = length(k_out);

julia> L_DBCM_reduced(θ, k_out, k_in, F, nz_out, nz_in, n);

```

```jldoctest
# Use with DBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> model_fun = θ -> L_DBCM_reduced(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, model.status[:d_unique]);

julia> model_fun(ones(size(model.θᵣ)))
-252.4627226503138
```
