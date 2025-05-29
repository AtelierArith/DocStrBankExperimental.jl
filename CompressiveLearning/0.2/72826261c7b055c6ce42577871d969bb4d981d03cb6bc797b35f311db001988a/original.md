Compressive `k`-means of the columns of `X`. Returns a matrix `C` whose columns are the centroids.

Supported keyword arguments include:

  * `m_factor`: the sketch size will be `m = m_factor × k × d` (independently of the type).
  * `kernel_var`: kernel variance
  * `decoder` (`:CLOMPR` or `:CLAMP`)
  * `decoder_kwargs`: dictionary of keyword arguments, passed to the decoder function
  * `out_dic`: output dictionary, useful parameters will be stored inside when provided

Supports also all the keyword arguments of [`skops_pair`](@ref).

See also [`weighted_CKM`](@ref).
