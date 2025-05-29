`UnivariateFeatureSelector` has the following fields:

  * `method::Function` (required)- Method to calculate feature importance. The method chosen will determine the scoring. Below is the scring with available statistical method to obtain them.

      * Correlation - higher score means more important

          * `pearson_correlation`
      * P-value - lower score means more important

          * `f_test`
          * `chisq_test`
  * `k::Union{Int64,Nothing}` - Select top `k` features with the highest correlation to target variable. You could ignore this by specifying k == nothing. This defaults to nothing.
  * `threshold::Union{Float64,Nothing}` - Select features with correlation more than or equal to threshold. To ignore, simply set threshold to nothing (default behavior).
