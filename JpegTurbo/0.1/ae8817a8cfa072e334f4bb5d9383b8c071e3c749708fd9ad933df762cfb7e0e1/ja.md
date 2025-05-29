```
jpeg_decode([T,] filename::AbstractString; kwargs...) -> Matrix{T}
jpeg_decode([T,] io::IO; kwargs...) -> Matrix{T}
jpeg_decode([T,] data::Vector{UInt8}; kwargs...) -> Matrix{T}
```

JPEG画像を色成分行列としてデコードします。ソースデータは、ファイル名、IO、またはメモリ内のバイトシーケンスのいずれかです。

# パラメータ

  * `transpose::Bool`: エンコードの前に画像の幅と高さの次元を入れ替える必要があるかどうか。デフォルト値は`false`です。
  * `scale_ratio::Real`: 画像を比率`scale_ratio`で`M/8`にスケールします。ここで`M ∈ 1:16`です。デフォルト値は`1`です。範囲外の値は最も近い値にマッピングされます。例えば、`0.3 => 2/8`および`0.35 => 3/8`です。`scale_ratio`と`preferred_size`は一緒に使用できません。
  * `preferred_size::Tuple`: `all(size(out) .>= preferred_size)`が成り立つ最小の`scale_ratio`を推測します。オプションで`(op, preferred_size)`形式にすることができ、比較演算子`op`は`>`, `>=`, `<`または`<=`のいずれかである必要があります。`op in (>=, >)`の場合、最小の`scale_ratio`が得られ、それ以外の場合は`op in (<=, <)`のための最大の`scale_ratio`が得られます。`scale_ratio`と`preferred_size`は一緒に使用できません。`preferred_size`の次元はキーワード`transpose`の影響を受けません。

# 例

```jldoctest
julia> using JpegTurbo, TestImages, ImageCore

julia> filename = testimage("earth", download_only=true);

julia> img = jpeg_decode(filename); summary(img)
"3002×3000 Matrix{RGB{N0f8}}"

julia> img = jpeg_decode(Gray, filename; scale_ratio=0.25); summary(img)
"751×750 Matrix{Gray{N0f8}}"
```

画像のプレビューや類似の目的のために、`T`と`scale_ratio`はJPEGデコードプロセスを加速するための有用なパラメータです。カラーJPEG画像の場合、`jpeg_decode(Gray, filename)`は`jpeg_decode(filename)`よりも高速です。なぜなら、カラー成分を処理する必要がないからです。小さい`scale_ratio`は、処理する必要のあるピクセルが少なく、より単純なIDCTメソッドを使用できるため、著しく高速なデコードを許可します。

```julia
using BenchmarkTools, TestImages, JpegTurbo
filename = testimage("earth", download_only=true)
# フルデコンプレッション
@btime jpeg_decode(filename); # 224.760 ms (7 allocations: 51.54 MiB)
# 輝度成分のみをデコンプレッション
@btime jpeg_decode(Gray, filename); # 91.157 ms (6 allocations: 17.18 MiB)
# ごく少数のピクセルのみを処理
@btime jpeg_decode(filename; scale_ratio=0.25); # 77.254 ms (8 allocations: 3.23 MiB)
# 輝度成分のためにごく少数のピクセルのみを処理
@btime jpeg_decode(Gray, filename; scale_ratio=0.25); # 63.119 ms (6 allocations: 1.08 MiB)
```
