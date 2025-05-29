```
Diag(A) -> NonuniformScaling(A)
```

は、引数をスケーリングファクター `A` で要素ごとに乗算する非一様スケーリング線形写像（タイプ `NonuniformScaling`）を生成します。この写像は *対角* 演算子と考えることができます。

`LinearAlgebra` の `diag` メソッドを呼び出すことで、スケーリングファクターを取得できます：

```
using LinearAlgebra
W = Diag(A)
diag(W) === A  # これは真です
```

!!! note
    [`Diag`](@ref)（大文字の 'D'）と [`diag`](@ref)（小文字の 'd'）メソッドの違いに注意してください。

