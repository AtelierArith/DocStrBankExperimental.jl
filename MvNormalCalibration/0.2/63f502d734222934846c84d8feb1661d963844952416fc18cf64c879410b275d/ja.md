```
sharpness(pred::Normal)
sharpness(pred::AbstractMvNormal)
```

正規分布（単変量または多変量）のシャープネスを計算します。シャープネスは、分布の標準偏差を含む楕円体の（ハイパー）体積として定義されます。

# 例

```julia-repl
julia> sharpness(Normal())
2
julia> sharpness(MvNormal(zeros(2), I(2)))  # 円の面積=πr^2を思い出してください
π
```
