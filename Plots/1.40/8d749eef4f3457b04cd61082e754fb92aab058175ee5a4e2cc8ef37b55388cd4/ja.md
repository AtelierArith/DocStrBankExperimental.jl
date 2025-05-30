```
histogram(x)
histogram!(x)
```

ヒストグラムをプロットします。

# 引数

  * `x`: ビンに分ける値の AbstractVector
  * `bins::Union{Integer, Symbol, Tuple{Integer, Integer},          AbstractVector}`: デフォルトは :auto (Freedman-Diaconis ルール)。ヒストグラムタイプの場合、目指すビンの概数を定義するか、使用する自動ビン分けアルゴリズムを指定します (:sturges,          :sqrt, :rice, :scott または :fd)。細かい制御が必要な場合は、ブレーク値のベクトルを渡します。例: `range(minimum(x),          stop = maximum(x), length = 25)`。エイリアス: (:bin, :nb,          :nbin, :nbins)。
  * `weights`: `x` の値に対する重みのベクトル、重み付きビンカウント用
  * `normalize::Union{Bool, Symbol}`: ヒストグラムの正規化モード。可能な値は: false/:none (正規化なし、デフォルト)、true/:pdf (離散PDFに正規化、ビンの合計面積が1になる)、:probability (ビンの高さの合計が1になる)、および :density (各ビンの面積がカウントに等しい - 不均一なビンサイズに便利)。エイリアス: (:norm, :normalized, :normalizes, :normed)。
  * `bar_position::Symbol`: `:overlay` (デフォルト) または `:stack` から選択します。(警告: 部分的にしか実装されていない可能性があります)。エイリアス: (:bar_positions, :barpositions)。
  * `bar_width::Real`: データ座標におけるバーの幅。`nothing` の場合、`x` (または `orientation = :h` の場合は `y`) に基づいて選択します。エイリアス: (:bar_widths, :barwidths)。
  * `bar_edges::Bool`: バーをエッジ (true) に揃えるか、センター (デフォルト) に揃えるか？。
  * `permute::Tuple{Symbol, Symbol}`: タプルで与えられた軸のデータと軸のプロパティを入れ替えます。例: (:x, :y)。エイリアス: (:permutes,).

# 例

```julia-repl
julia> histogram([1,2,1,1,4,3,8],bins=0:8)
julia> histogram([1,2,1,1,4,3,8],bins=0:8,weights=weights([4,7,3,9,12,2,6]))
```
