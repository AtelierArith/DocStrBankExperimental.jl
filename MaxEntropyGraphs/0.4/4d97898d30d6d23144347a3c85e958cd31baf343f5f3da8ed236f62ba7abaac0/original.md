```
initial_guess(m::UBCM, method::Symbol=:degrees)
```

Compute an initial guess for the maximum likelihood parameters of the UBCM model `m` using the method `method`.

The methods available are: 

  * `:degrees` (default): the initial guess is computed using the degrees of the graph, i.e. $\theta_{i} = -\log(d_{i})$
  * `:degrees_minor`: the initial guess is computed using the degrees of the graph and the number of edges, i.e. $\theta_{i} = -\log(d_{i}/(\sqrt{E} + 1))$
  * `:random`: the initial guess is computed using random values between 0 and 1, i.e. $\theta_{i} = -\log(r_{i})$ where $r_{i} \sim U(0,1)$
  * `:uniform`: the initial guess is uniformily set to 0.5, i.e. $\theta_{i} = -\log(0.5)$
  * `:chung_lu`: the initial guess is computed using the degrees of the graph and the number of edges, i.e. $\theta_{i} = -\log(d_{i}/(2E))$

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:degrees_minor);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model)
11-element Vector{Float64}:
 -0.0
 -0.6931471805599453
 -1.0986122886681098
 -1.3862943611198906
 -1.6094379124341003
 -1.791759469228055
 -2.1972245773362196
 -2.302585092994046
 -2.4849066497880004
 -2.772588722239781
 -2.833213344056216

```
