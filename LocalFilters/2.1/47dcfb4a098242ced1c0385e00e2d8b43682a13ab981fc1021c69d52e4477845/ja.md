```
LocalFilters.ball(Dims{N}, r)
```

は半径 `r` の `N` 次元ボールを近似するマスクを生成します。結果は、すべての次元が奇数で等しいブール値の `N` 次元配列で、ボールの内部（中心からの距離 `≤ r` の場所）では `true`、それ以外では `false` となります。このマスクは、局所フィルタリング操作における近傍、カーネル、または構造要素を指定するために使用できます。

返されるマスクは中心軸を持っており、1ベースのインデックスを持つマスクを取得するには、次のように呼び出します：

```
LocalFilters.ball(Dims{N}, r).parent
```

さらに [`LocalFilters.kernel`](@ref) と [`LocalFilters.strel`](@ref) も参照してください。
