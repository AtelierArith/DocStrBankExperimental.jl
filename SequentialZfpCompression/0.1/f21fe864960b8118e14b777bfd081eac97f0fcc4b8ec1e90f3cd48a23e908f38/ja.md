```
SeqCompressor(dtype::DataType, spacedim::Integer...;
              rate::Int=0, tol::Real=0, precision::Real=0,
              filepaths::Union{Vector{String}, String}="",
              envVarPath::String="")
```

引数に応じて `CompressedArraySeq` または `CompressedMultiFileArraySeq` を構築します。

# 引数

  * `dtype::DataType`: 圧縮される配列の型
  * `spacedim::Integer...`: 圧縮される配列の次元
  * `inmemory::Bool=true`: 圧縮データがメモリに保存されるかディスクに保存されるか
  * `rate::Int64`: [値ごとに使用されるビット数を固定します](https://zfp.readthedocs.io/en/release0.5.5/modes.html#fixed-rate-mode)。
  * `tol::Float32`: [許容される平均絶対誤差](https://zfp.readthedocs.io/en/release0.5.5/modes.html#fixed-accuracy-mode)。
  * `precision::Float32`: [精度を制御し、弱い相対誤差を制限します](https://zfp.readthedocs.io/en/release0.5.5/modes.html#fixed-precision-mode)。
  * `filepaths::Union{Vector{String}, String}=""`: 圧縮されるファイルへのパス
  * `envVarPath::String=""`: 圧縮されるファイルへのパスを含む環境変数の名前

環境変数、ファイルパス、ファイルパスのベクトル、または何も渡さないオプションがあります。ファイルパスのベクトルを渡す場合、パスの数はスレッドの数と等しくなければなりません。単一のファイルパスを渡す場合、すべてのスレッドで同じパスが使用されます。環境変数を渡す場合、ファイルパスはそこから抽出されます。たとえば、SLURMジョブスケジューラを使用している場合、ノードのローカルディスクにアクセスできるため便利です（`ENV["SLURM_TMPDIR"]`を使用）。

# 例

```jldoctest
julia> using SequentialZfpCompression

julia> A = SeqCompressor(Float64, 4, 4)
SequentialZfpCompression.CompressedArraySeq{Float64, 2}(UInt8[], [0], [0], (4, 4), 0, Float64, 0.0f0, 0, 0)

julia> A.timedim
0

julia> size(A)
(4, 4, 0)

julia> append!(A, ones(Float64, 4, 4));

julia> A[1]
4×4 Matrix{Float64}:
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0

julia> size(A)
(4, 4, 1)
```
