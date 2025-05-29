```
initial_guess(m::BiCM; method::Symbol=:degrees)
```

Compute an initial guess for the maximum likelihood parameters of the BiCM model `m` using the method `method`.

The methods available are: 

  * `:degrees` (default): the initial guess is computed using the degrees of the graph, i.e. $\theta = [-\log(d_{ot}); -\log(d_{	op})]$
  * `:random`: the initial guess is computed using random values between 0 and 1, i.e. $\theta_{i} = -\log(r_{i})$ where $r_{i} \sim U(0,1)$
  * `:uniform`: the initial guess is uniformily set to 0.5, i.e. $\theta_{i} = -\log(0.5)$
  * `:chung_lu`: the initial guess is computed using the degrees of the graph and the number of edges, i.e. $\theta = [-\log(d_{ot}/(2E)); -\log(d_{	op}/(2E))]$

# Examples

```jldoctest
julia> model = BiCM(corporateclub());

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model);

```
