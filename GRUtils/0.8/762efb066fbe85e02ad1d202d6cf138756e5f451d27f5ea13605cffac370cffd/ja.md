```
oplot(args...; kwargs...)
```

別のプロットの上に1つ以上の線グラフを描画します。

現在のプロットを保持した後に[`plot`](@ref)を呼び出すのと同等ですが、軸の制限は新しいデータに合わせて再調整されません。

# 例

```julia
# サンプルデータを作成
x = LinRange(-2, 2, 40)
y = 2 .* x .+ 4
# 最初のプロットを描画
plot(x, y)
# その上に別のグラフをプロット
oplot(x, x -> x^3 + x^2 + x)

```
