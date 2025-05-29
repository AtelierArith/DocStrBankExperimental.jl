```
ExploreSettings(
    domains;
    complete_search_limit = 10^6,
    max_samplings = sum(domain_size, domains),
    search = :flexible,
    solutions_limit = floor(Int, sqrt(max_samplings)),
)
```

Create settings for the exploration of a search space composed by a collection of domains.

# Arguments

  * `domains`: A collection of domains representing the search space.
  * `complete_search_limit`: Maximum size of the search space for complete search.
  * `max_samplings`: Maximum number of samples to take during partial search.
  * `search`: Search strategy (`:flexible`, `:complete`, or `:partial`).
  * `solutions_limit`: Maximum number of solutions to store.

# Returns

An `ExploreSettings` object.

# Example

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
settings = ExploreSettings(domains, search = :complete)
```
