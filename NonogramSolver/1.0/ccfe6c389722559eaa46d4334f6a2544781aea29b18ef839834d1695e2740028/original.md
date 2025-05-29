Holds intermediate quantities describing the [`Puzzle`](@ref) `p`.

These quantities are used by [`solve_puzzle`](@ref) to solve a puzzle. Quantities are named as in Khan's article (2022, doi:10.1109/TG.2020.3036687), and their purposes are described there.

# Fields

  * `sigmaR::Array{Int, 2}`: Spacing quantities for blocks in rows.
  * `sigmaC::Array{Int, 2}`: Spacing quantities for blocks in columns.
  * `fSetR::Array{UnitRange{Int}, 2}`: First-position sets for blocks in rows.
  * `fSetC::Array{UnitRange{Int}, 2}`: First-position sets for blocks in columns.
  * `oSetR::Array{UnitRange{Int}, 3}`: Overlap-checking sets for blocks in rows.
  * `oSetC::Array{UnitRange{Int}, 3}`: Overlap-checking sets for blocks in columns.
  * `mSetR::Array{Vector{Int}, 2}`: Monochrome index sets for rows.
  * `mSetC::Array{Vector{Int}, 2}`: Monochrome index sets for columns.
  * `maxBR::Int`: Upper bound on number of blocks in each row.
  * `maxBC::Int`: Upper bound on number of blocks in each column.
