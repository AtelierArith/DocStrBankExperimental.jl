```
place_knvd(A::AbstractMatrix, B, λ; verbose = false, init = :s)
```

ロバストポール配置は、次のアルゴリズムを使用しています。

> "ロバストポールアサインメントにおける線形状態フィードバック", Kautsky, Nichols, Van Dooren


この実装では、Xステップに「メソッド0」を使用し、すべての因数分解にQR因数分解を使用します。

この関数は、MIMOシステムで[`place`](@ref)が呼び出されると自動的に呼び出されます。

# 引数:

  * `init`: `X`行列を見つけるための反復の初期化戦略を決定します。可能な選択肢は`:id`（デフォルト）、`:rand`、`:s`です。
