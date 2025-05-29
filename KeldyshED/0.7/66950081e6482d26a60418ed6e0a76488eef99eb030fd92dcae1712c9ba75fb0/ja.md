```julia
c_connection(
    ed::KeldyshED.EDCore,
    op_linear_index::Int64,
    sp_index::Int64
) -> Union{Nothing, Int64}

```

消滅演算子によって生成されたサブスペースからサブスペースへの接続を、厳密対角化ソルバーから抽出します。接続が存在しない場合は `nothing` を返します。

## 引数

  * `ed`:              厳密対角化ソルバーオブジェクト。
  * `op_linear_index`: `ed.full_hs.soi` によって定義された消滅演算子の線形インデックス。
  * `sp_index`:        初期サブスペースインデックス。
