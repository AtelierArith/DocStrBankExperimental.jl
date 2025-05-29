```
compute_coefficients(func, t, semi::AbstractSemidiscretization)
```

連続関数 `func` の離散係数を、半離散化 `semi` に関連する時刻 `t` で計算します。例えば、離散的ガレルキンスペクトル要素法（[`DGSEM`](@ref)）の `func` の離散係数は、ロバット・ルジャンドルノードでの `func` の値です。同様に、古典的な有限差分法は、半離散化 `semi` に関連するグリッドのノードでの `func` の値を使用します。

初期条件に関連する半離散化 `semi` の場合、時刻 `t` で与えられた初期条件を使用するために `func` を省略できます。
