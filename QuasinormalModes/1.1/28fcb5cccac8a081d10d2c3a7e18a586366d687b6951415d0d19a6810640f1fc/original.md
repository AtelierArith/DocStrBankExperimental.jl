Cache of coefficient arrays for the AIM. To each AIM problem corresponds a cache. As long as the problem doesn't change, the cache can be reused.

# Members

  * `icda::Array{T,1}`: Hold the initial c data, i.e., c^i_0.
  * `ccda::Array{T,1}`: Hold the coefficients for the current aim step, c^i_n.
  * `pcda::Array{T,1}`: Hold the coefficients for the previous aim step, c^i_{n-1}.
  * `bcda::Array{T,1}`: The work buffer used to actually compute the c coefficients in parallel.
  * `idda::Array{T,1}`: Hold the initial d data, i.e., c^i_0.
  * `cdda::Array{T,1}`: Hold the coefficients for the current aim step, d^i_n.
  * `pdda::Array{T,1}`: Hold the coefficients for the previous aim step, d^i_{n-1}.
  * `bdda::Array{T,1}`: The work buffer used to actually compute the d coefficients in parallel.
  * `size::N`: The size of the arrays in the cache.
