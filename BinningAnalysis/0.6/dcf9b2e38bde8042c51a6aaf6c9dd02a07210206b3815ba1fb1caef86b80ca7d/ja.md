```
ErrorPropagator(zero_element::T...[; capacity::Int])
```

新しい `ErrorPropagator` を作成します。これは、各入力の型 `T` に対して（少なくとも）`capacity` 個の値を取ることができます。型とサイズは、与えられた `zero_element` から継承され、これらはすべてゼロでなければなりません。

値は `push!` と `append!` を使用して追加できます。

---

```
ErrorPropagator(timeseries::AbstractVector{T}...)
```

新しい `ErrorPropagator` を作成し、各指定されたタイムシリーズからすべての要素を追加します。
