```
stem(x[, y, spec; kwargs...])
stem(x1, y1, x2, y2...; kwargs...)
stem(x1, y1, spec1...; kwargs...)
```

茎プロットを描画します

茎とマーカーの座標と形式は、線プロットと同様に定義されています（cf. [`plot`](@ref)）。

さらに、キーワード引数 `baseline` を使用して、茎が開始するY座標を定義できます。

# 例

```julia
# 例データを作成
x = LinRange(-2, 2, 40)
y = x.^3 .+ x.^2 .+ x .+ 6
# xとyをプロットし、星で終わる破線の茎を描画
stem(x, y, "--p")
# ベースラインを5に移動
stem(x, y, baseline = 5)

```
