```
MixedInteger(algorithm; information = Information(), options = Options())
```

Create a wrapper to enable an `algorithm` to handle mixed-integer problems. When `MixedInteger` is used, the objective function will receive a dictionary with values in corresponding search space.

# Example

```julia

# objective function
f(solution) = sum(solution[:integer]) * (1 .- sum(solution[:continuous])^2 )

# search spaces
integer_space = BoxConstrainedSpace(-10ones(Int, 6), 10ones(Int, 6))
continuous_space = BoxConstrainedSpace(-ones(3), ones(3))
# mix spaces to form a mixed space
mixed_space = MixedSpace(:integer => integer_space, :continuous => continuous_space)

# wrap ECA to handle mixed-integer variables
mip_eca = MixedInteger(ECA(N = 100), options = Options(seed = 1))

result = optimize(f, mixed_space, mip_eca)

# convert resulting minimizer (which is a vector) into a dictionary
solution = Metaheuristics.vec_to_dict(minimizer(result), mixed_space)
display(solution)
```

**output**

```julia
Dict{Symbol, Vector} with 2 entries:
  :continuous => [-1.0, -1.0, -1.0]
  :integer    => [10, 10, 10, 10, 10, 10]
```
