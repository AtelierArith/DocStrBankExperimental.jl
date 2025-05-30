```
fit_gambin(community_matrix::Community_Matrix, community_selected::String)
```

Fit a Gamma Binomial (GamBin) model to a species abundance distribution.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data.
  * `community_selected::String`: The name of the community for which the model will be fitted.

# Returns

  * The optimized parameter (α) of the Gamma Binomial model.

# Details

The function fits a Gamma Binomial (GamBin) model to the species abundance distribution of the selected community.  The model is fitted using maximum likelihood estimation to find the optimal value of the parameter (α) that maximizes the likelihood of observing the given abundance distribution under the GamBin model. 

See also [`octave`](@ref), [`octave_plot`](@ref), [`fit_gambin_plot`](@ref)

# Reference

Ugland, K. I., Lambshead, P. J. D., McGill, B., Gray, J. S., O’Dea, N., Ladle, R. J., & Whittaker, R. J. (2007). Modelling dimensionality in species abundance distributions: Description and evaluation of the Gambin model. Evolutionary Ecology Research, 9(2), 313–324.

Matthews, T. J., Borregaard, M. K., Ugland, K. I., Borges, P. A. V., Rigal, F., Cardoso, P., & Whittaker, R. J. (2014). The gambin model provides a superior fit to species abundance distributions with a single free parameter: Evidence, implementation and interpretation. Ecography, 37(10), 1002–1011. https://doi.org/10.1111/ecog.00861
