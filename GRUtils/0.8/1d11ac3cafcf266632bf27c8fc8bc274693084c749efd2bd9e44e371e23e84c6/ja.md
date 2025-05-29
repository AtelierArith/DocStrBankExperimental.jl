```
colormap!(p, cmap)
```

与えられたプロット `p` に colormap `cmap` を適用します。`p` は `PlotObject` または `Figure` であり（この場合、colormap はそれに含まれるすべてのプロットに適用されます）。

`cmap` の値は、任意の [GR 組み込み colormap](https://gr-framework.org/colormaps.html) の番号または名前であることができます（詳細については [`colormap`](@ref) を参照してください）。

プロット関数でキーワード引数 `colormap` を使用して、プロットの作成中に特定の colormap を設定します（この場合、番号でのみ識別できます）。

# 例

```julia
# "grayscale" colormap (2) を使用してサーフェスプロットを作成
surface(x, y, z, colormap=2)
# "viridis" colormap に変更
colormap!(gcf(), "viridis")
```
