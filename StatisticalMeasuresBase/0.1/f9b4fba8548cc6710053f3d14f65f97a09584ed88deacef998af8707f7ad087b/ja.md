```
aggregate(itr; weights=nothing, mode=Mean(), skipnan=false)
```

イテレータ `itr` によって生成された値を、指定された集約 `mode` とオプションで指定された数値 `weights` を使用して集約します。

`itr` にある `missing` 値は集約の前にスキップされますが、正規化因子にはまだカウントされます。したがって、戻り値の型にゼロがある場合、`missing` をゼロで置き換えたかのようになります。

集約される値は、`+`、`*`、`/` および `^`（`RootMean` の場合）が定義されている型を共有する必要があります。または、値型がそのように装備された辞書である必要があります。

# キーワードオプション

  * `weights=nothing`: `length` を持つイテレータで、`Real` 要素を生成するか、または `nothing`
  * `mode=Mean()`: オプションには `Mean()` と `Sum()` が含まれます。すべてのオプションとその意味については [`StatisticalMeasuresBase.AggregationMode`](@ref) を参照してください。`Mean()` を重みと組み合わせて使用すると、通常の加重平均が平均重み値でスケーリングされて返されます。
  * `skipnan=false`: `missing` 値に加えて `NaN` 値をスキップするかどうか
  * `aggregate=true`: `false` の場合、`itr` は指定された重みで単に乗算され、収集されます。

# 例

3 倍の交差検証アルゴリズムが以下の `errors` によって与えられる二乗平均平方根誤差を提供し、フォールドが指定された `sizes` を持つとします。次に、以下の `μ` は適切な誤差の集約です。

```julia
errors = [0.1, 0.2, 0.3]
sizes = [200, 200, 150]
weights = 3*sizes/sum(sizes)
@assert mean(weights) ≈ 1
μ = aggregate(errors; weights, mode=RootMean())
@assert μ ≈ (200*0.1^2 + 200*0.2^2 + 150*0.3^2)/550 |> sqrt
```

---

```
aggregate(f, itr; options...)
```

代わりに、`itr` に対して `f` をブロードキャストした結果を集約します。重みの乗算はブロードキャスト操作と融合されているため、このメソッドは別々にブロードキャスト、重み付け、集約するよりも効率的です。

このメソッドは、上記と同じキーワード `options` を持っています。

# 例

```julia
itr = [(1, 2), (2, 3), (4, 3)]

julia> aggregate(t -> abs(t[1] - t[2]), itr, weights=[10, 20, 30], mode=Sum())
60
```
