```
isosurface(data, isovalue; kwargs...)
```

与えられた `isovalue` の周りの三次元配列 `data` の領域によって決定される等値面を描画します。

等値面は、`data` の値が `isovalue` より大きい場合は表面の外側と見なされ、`isovalue` より小さい値は表面の内側と見なされるように計算されます。

等値面の色は、キーワード引数 `color` を使用して選択でき、16進数のRGBカラーコードを指定します。

# 例

```julia
# サンプルデータを作成
s = LinRange(-4, 4, 50)
v = cos.(s) .+ cos.(s)' .+ cos.(reshape(s,1,1,:))
# 等値面を描画
isosurface(v, 0.5, color=0x99ffcc)

```
