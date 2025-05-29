```julia
histcounts(x, y, xedges::AbstractRange, yedges::AbstractRange; T=Int64, normalize=false)
```

`NaN`を無視した2Dヒストグラム：`x, y`のペアが、`xedges`と`yedges`で指定された等間隔の正方形のビンの2Dグリッドの各正方形に落ちる数を計算します。

結果として得られるカウントの行列`N`は、最も低いxおよびyビンが`N[1,1]`に配置され、`N`の最初の（垂直/行）次元はy軸に対応し（`size(N,1) == length(yedges)-1`）、2番目の（水平/列）次元はx軸に対応します（`size(N,2) == length(xedges)-1`）。

デフォルトでは、カウントは`Int64`として返されますが、オプションのキーワード引数`T`を指定することで出力タイプを変更できます。

## 例

```julia
julia> x = y = 0.5:9.5;

julia> xedges = yedges = 0:10;

julia> N = histcounts(x,y,xedges,yedges)
10×10 Matrix{Int64}:
 1  0  0  0  0  0  0  0  0  0
 0  1  0  0  0  0  0  0  0  0
 0  0  1  0  0  0  0  0  0  0
 0  0  0  1  0  0  0  0  0  0
 0  0  0  0  1  0  0  0  0  0
 0  0  0  0  0  1  0  0  0  0
 0  0  0  0  0  0  1  0  0  0
 0  0  0  0  0  0  0  1  0  0
 0  0  0  0  0  0  0  0  1  0
 0  0  0  0  0  0  0  0  0  1
```
