```
LogBinner(zero_element::T[; capacity::Int])
```

新しい `LogBinner` を作成します。これは、型 `T` の値を (少なくとも) `capacity` 個受け取ることができます。型とサイズは、与えられた `zero_element` から継承され、これは専らゼロを含む必要があります。

値は `push!` と `append!` を使用して追加できます。

---

```
LogBinner(timeseries::AbstractVector{T})
```

新しい `LogBinner` を作成し、与えられた時系列からすべての要素を追加します。
