```
biodiversity_surface(community_matrix::Community_Matrix)
```

Create a biodiversity surface plot for a community matrix.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data for multiple communities.

# Returns

  * A Makie Figure representing the biodiversity surface plot.

# Details

The function generates a 3D surface plot using Makie to visualize biodiversity across communities.  It computes the Hill series for each community using the `BioExplorer.hill` function and plots the equivalent number of species against the order of Hill number.  The x-axis represents different communities, the y-axis represents the order of Hill number, and the z-axis represents the equivalent number of species.  Different colors on the surface indicate variations in biodiversity across communities.

See also [`hill`](@ref)
