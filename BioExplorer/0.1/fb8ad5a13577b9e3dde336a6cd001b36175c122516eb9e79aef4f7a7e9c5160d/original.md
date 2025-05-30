```
generate_abundance_communities(nb_species::Int64, nb_sites::Int64, poisson_lambda::Number = Float64(50))
```

Generate a fake community matrix with abundance data using Poisson distribution.

# Arguments

  * `nb_species::Int64`: The number of species in each community.
  * `nb_sites::Int64`: The number of sites (communities).
  * `poisson_lambda::Number`: The lambda parameter for the Poisson distribution used to generate abundance data. Defaults to 50.

# Returns

  * A community matrix containing randomly generated abundance data.

# Details

The function generates a fake community matrix with abundance data by randomly sampling species abundances from a Poisson distribution. Each row of the matrix represents a site (community), and each column represents a species. The abundance data is rounded to the nearest integer.  The default value of the lambda parameter for the Poisson distribution is set to 50.

See also [`generate_incidence_communities`](@ref)
