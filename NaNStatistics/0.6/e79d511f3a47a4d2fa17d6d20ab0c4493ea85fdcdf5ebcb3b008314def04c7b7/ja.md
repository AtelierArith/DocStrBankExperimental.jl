```julia
histcounts(x, xedges::AbstractRange; T=Int64, normalize=false)
```

1D ヒストグラム、`NaN` を無視します：`x` 軸に沿った `length(xedges)-1` の等間隔のビンに落ちる `x` 値の数を計算します。ビンの境界は `xedges` で指定されます。

デフォルトでは、カウントは `Int64` として返されますが、オプションのキーワード引数 `T` を指定することで出力タイプを変更できます。

## 例

```julia
julia> b = 10 * rand(100000);

julia> histcounts(b, 0:1:10)
10-element Vector{Int64}:
 10054
  9987
  9851
  9971
  9832
 10033
 10250
 10039
  9950
 10033
```
