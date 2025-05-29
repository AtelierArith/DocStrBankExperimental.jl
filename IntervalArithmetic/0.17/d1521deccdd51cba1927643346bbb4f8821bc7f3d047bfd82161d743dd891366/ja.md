```
intersect(a::Interval{T}...) where T
```

引数のn-元交差を返します。

この関数は、`intersect(a1, a2, a3, a4)`のように、任意の数の入力区間に適用可能です。入力をスプラットする必要がある場合は、`intersect(a...)`の代わりに`reduce(intersect, a)`を検討してください。スプラットのコストを節約できます。
