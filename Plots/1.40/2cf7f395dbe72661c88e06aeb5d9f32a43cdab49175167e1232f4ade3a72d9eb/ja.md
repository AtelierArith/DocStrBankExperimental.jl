```
boxplot(x, y)
boxplot!(x, y)
```

箱ひげ図を作成します。

# キーワード引数

  * `notch`: Bool. 箱ひげ図にノッチを付けますか？ (false)
  * `whisker_range`: 実数。ひげは第一四分位数の下と第三四分位数の上に `whisker_range`*IQR だけ延びます。この範囲外の値は外れ値として表示されます (1.5)
  * `outliers`: Bool. 外れ値を表示しますか？ (true)
  * `whisker_width`: 実数またはシンボル。ひげの長さ；オプションは箱の幅に合わせる `:match`、`：half`、または合計の長さを示す数値です。 (:half)

# 例

```julia-repl
julia> using StatsPlots
julia> boxplot(repeat([1,2,3],outer=100),randn(300))
```
