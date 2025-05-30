```
octave_plot(community_matrix::Community_Matrix, community_selected::String)
```

Display the Octave plot of a selected community.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.
  * `community_selected::String`: The name of the community for which the Octave plot is to be displayed.

# Returns

  * Makie Figure representing the Octave plot.

# Details

This function computes the octave distribution of species abundance within a selected community using the `octave` function and displays it as a bar plot.  Each bar in the plot represents an octave class, with the x-axis indicating the octave class and the y-axis indicating the number of species falling within each octave class.

See also [`octave`](@ref),
