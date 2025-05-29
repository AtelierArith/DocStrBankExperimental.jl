```julia
monomial_connection(
    ed::KeldyshED.EDCore,
    mon::KeldyshED.Operators.Monomial,
    sp_index::Int64
) -> Union{Nothing, Int64}

```

モノミアル演算子（正準演算子 $c$/$c^\dagger$ の積）によって生成される部分空間間の接続を、厳密対角化ソルバーから抽出します。接続が存在しない場合は `nothing` を返します。

## 引数

  * `ed`:       厳密対角化ソルバーオブジェクト。
  * `mon`:      問題のモノミアル。
  * `sp_index`: 初期部分空間インデックス。
