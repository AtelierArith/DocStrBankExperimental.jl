```
SVG([output::Union{IO,AbstractString}], width=√200cm, height=10cm, jsmode=:none) -> Backend
```

スケーラブルベクターグラフィックバックエンドを作成します。出力は通常[`draw`](@ref)に渡されます。最初の引数として文字列を使用してファイル名を指定します。`jsmode`は`:none`、`:embed`、`:linkabs`、または`:linkrel`のいずれかにすることができます。詳細は[`SVGJS`](@ref)を参照してください。

# 例

```
c = compose(context(), line())
draw(SVG("myplot.svg"), c)
```
