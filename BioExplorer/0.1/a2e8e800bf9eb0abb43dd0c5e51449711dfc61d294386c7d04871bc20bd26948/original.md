```
generate_incidence_communities(nb_species::Int64, nb_sites::Int64, probability::Number = Float64(50))
```

Generate a fake community matrix with incidence data using a Binomial distribution.

# Arguments

  * `nb_species::Int64`: The number of species in each community.
  * `nb_sites::Int64`: The number of sites (communities).
  * `probability::Number`: The probability parameter for the Binomial distribution used to generate incidence data. Defaults to 50.

# Returns

  * A community matrix containing randomly generated incidence data.

# Details

The function generates a fake community matrix with incidence data by randomly sampling species presence/absence using a Binomial distribution.  Each row of the matrix represents a site (community), and each column represents a species.  The incidence data is rounded to the nearest integer (0 or 1).  The default value of the probability parameter for the Binomial distribution is set to p = 0.5.

See also [`generate_abundance_communities`](@ref)
