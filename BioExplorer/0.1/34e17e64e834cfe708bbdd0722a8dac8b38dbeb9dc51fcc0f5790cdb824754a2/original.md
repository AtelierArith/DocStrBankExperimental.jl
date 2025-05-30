```
whittacker_plot(community_matrix::Community_Matrix, community_selected::String)
```

Display the Whittaker plot of a selected community.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.
  * `community_selected::String`: The name of the community for which the Whittaker plot is to be displayed.

# Returns

  * Makie Figure representing the Whittaker plot.

# Details

This function generates a Whittaker plot for the selected community from the input community matrix.  The plot shows the log10 abundance of species against their rank.  The species are ranked by abundance, and the abundance is plotted on the y-axis in log10 scale.  The rank of each species is plotted on the x-axis.

See also [`rank`](@re, [`octave_plot`](@ref)
