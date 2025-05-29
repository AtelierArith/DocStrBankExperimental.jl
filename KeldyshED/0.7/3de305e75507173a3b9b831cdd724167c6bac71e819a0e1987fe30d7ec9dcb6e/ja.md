```julia
cdag_connection(
    ed::KeldyshED.EDCore,
    op_linear_index::Int64,
    sp_index::Int64
) -> Union{Nothing, Int64}

```

生成演算子によって生成された部分空間から部分空間への接続を、厳密対角化ソルバーから抽出します。接続が存在しない場合は `nothing` を返します。

## 引数

  * `ed`:              厳密対角化ソルバーオブジェクト。
  * `op_linear_index`: `ed.full_hs.soi` によって定義された生成演算子の線形インデックス。
  * `sp_index`:        初期部分空間インデックス。
