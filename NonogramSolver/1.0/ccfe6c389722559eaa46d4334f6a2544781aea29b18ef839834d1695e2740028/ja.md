中間量を保持し、[`Puzzle`](@ref) `p`を記述します。

これらの量は、パズルを解くために[`solve_puzzle`](@ref)によって使用されます。量はKhanの論文（2022年、doi:10.1109/TG.2020.3036687）に記載されているように名付けられており、その目的もそこで説明されています。

# フィールド

  * `sigmaR::Array{Int, 2}`: 行のブロックの間隔量。
  * `sigmaC::Array{Int, 2}`: 列のブロックの間隔量。
  * `fSetR::Array{UnitRange{Int}, 2}`: 行のブロックのための最初の位置セット。
  * `fSetC::Array{UnitRange{Int}, 2}`: 列のブロックのための最初の位置セット。
  * `oSetR::Array{UnitRange{Int}, 3}`: 行のブロックのための重複チェックセット。
  * `oSetC::Array{UnitRange{Int}, 3}`: 列のブロックのための重複チェックセット。
  * `mSetR::Array{Vector{Int}, 2}`: 行のためのモノクロームインデックスセット。
  * `mSetC::Array{Vector{Int}, 2}`: 列のためのモノクロームインデックスセット。
  * `maxBR::Int`: 各行のブロックの最大数の上限。
  * `maxBC::Int`: 各列のブロックの最大数の上限。
