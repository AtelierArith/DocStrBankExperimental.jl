```
initial_guess(m::DBCM, method::Symbol=:degrees)
```

Compute an initial guess for the maximum likelihood parameters of the DBCM model `m` using the method `method`.

The methods available are: 

  * `:degrees` (default): the initial guess is computed using the degrees of the graph, i.e. $\theta = [-\log(d_{out}); -\log(d_{in})]$
  * `:degrees_minor`: the initial guess is computed using the degrees of the graph and the number of edges, i.e. $\theta = [-\log(d_{out}/(\sqrt{E} + 1)); -\log(d_{in}//(\sqrt{E} + 1) )]$
  * `:random`: the initial guess is computed using random values between 0 and 1, i.e. $\theta_{i} = -\log(r_{i})$ where $r_{i} \sim U(0,1)$
  * `:uniform`: the initial guess is uniformily set to 0.5, i.e. $\theta_{i} = -\log(0.5)$
  * `:chung_lu`: the initial guess is computed using the degrees of the graph and the number of edges, i.e. $\theta = [-\log(d_{out}/(2E)); -\log(d_{in}/(2E))]$

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:degrees_minor);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model);

```
