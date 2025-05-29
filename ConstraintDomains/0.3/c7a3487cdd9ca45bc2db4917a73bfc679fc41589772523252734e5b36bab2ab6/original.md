```
explore(domains, concept; settings = ExploreSettings(domains), parameters...)
```

Explore a search space defined by domains and a concept.

# Arguments

  * `domains`: A collection of domains representing the search space.
  * `concept`: The concept function defining the constraint.
  * `settings`: An `ExploreSettings` object to configure the exploration process.
  * `parameters`: Additional parameters to pass to the concept function.

# Returns

A tuple containing two sets: (solutions, non_solutions).

# Example

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
solutions, non_solutions = explore(domains, allunique)
```
