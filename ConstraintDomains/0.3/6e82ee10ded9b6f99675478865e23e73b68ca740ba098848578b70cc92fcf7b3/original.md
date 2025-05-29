Explorer(concepts, domains, objective = nothing; settings = ExploreSettings(domains))

Create an Explorer object for searching a constraint satisfaction problem space.

# Arguments

  * `concepts`: A collection of tuples, each containing a concept function and its associated variable indices.
  * `domains`: A collection of domains representing the search space.
  * `objective`: An optional objective function for optimization problems.
  * `settings`: An `ExploreSettings` object to configure the exploration process.

# Returns

An `Explorer` object ready for exploration.

# Example

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
concepts = [(sum, [1, 2])]
objective = x -> x[1] + x[2]
explorer = Explorer(concepts, domains, objective)
```
