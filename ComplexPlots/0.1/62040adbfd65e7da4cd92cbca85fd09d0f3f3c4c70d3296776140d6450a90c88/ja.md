zplot(f, z; coloring=artist()) zplot(f, xlims=[-4, 4], ylims=[-4, 4], n=800; coloring=artist()) 複素値関数 `f` を行列 `z` の点で評価するか、複素平面の `xlims`×`ylims` 上の `n`×`n` グリッドで評価します。値の色付け方法はキーワード引数 `coloring` によって指定されます。

zplot(z; coloring=artist()) 複素値の行列を、キーワード引数 `coloring` で指定された関数に従って色付けしてプロットします。`z` は複素平面のグリッドで評価された結果であると仮定されます。

# 例

```julia
zplot(z -> (z^3 - 1) / sin(2im - z))
zplot(tanh)
zplot(tanh, coloring=artist(1.5))  # より多くの大きさの等高線を見るため
```
