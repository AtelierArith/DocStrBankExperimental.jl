```
fit_gambin_plot(community_matrix::Community_Matrix, community_selected::String)
```

Plot the species abundance distribution and the fitted Gamma Binomial (GamBin) model.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data.
  * `community_selected::String`: The name of the community for which the model will be fitted and plotted.

# Returns

  * A Makie Figure representing the plot of species abundance distribution and the fitted GamBin model.

# Details

The function plots the species abundance distribution of the selected community along with the fitted Gamma Binomial (GamBin) model.  It first fits the GamBin model using the `fit_gambin` function to obtain the optimized parameter (α), and then plots the observed abundance distribution as a bar plot and the fitted model as a line plot on the same axis.  The resulting Makie Figure represents the plot of species abundance distribution and the fitted GamBin model.

See also [`octave`](@ref), [`octave_plot`](@ref), [`fit_gambin`](@ref)

# Reference

Ugland, K. I., Lambshead, P. J. D., McGill, B., Gray, J. S., O’Dea, N., Ladle, R. J., & Whittaker, R. J. (2007). Modelling dimensionality in species abundance distributions: Description and evaluation of the Gambin model. Evolutionary Ecology Research, 9(2), 313–324.

Matthews, T. J., Borregaard, M. K., Ugland, K. I., Borges, P. A. V., Rigal, F., Cardoso, P., & Whittaker, R. J. (2014). The gambin model provides a superior fit to species abundance distributions with a single free parameter: Evidence, implementation and interpretation. Ecography, 37(10), 1002–1011. https://doi.org/10.1111/ecog.00861
