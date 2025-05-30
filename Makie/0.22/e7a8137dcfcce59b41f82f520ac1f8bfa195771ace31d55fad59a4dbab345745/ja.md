```
Categorical(colormaplike)
```

プロットの `colormap` 属性が受け入れるすべてのカラーマップ値を受け入れます。1つの値を1つの色にマッピングし、プロットの正しいカラーバーを作成することを保証します。

例:

```julia
fig, ax, pl = barplot(1:3; color=1:3, colormap=Makie.Categorical(:viridis))
```

!!! 警告     この機能は、APIがまだ最終化されていないため、破壊的なリリースの外で変更される可能性があります。
