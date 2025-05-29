```julia
c_connection(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}},
    sp_index::Int64
) -> Union{Nothing, Int64}

```

消滅演算子によって生成されたサブスペース間の接続を、厳密対角化ソルバーから抽出します。該当する接続が存在しない場合は `nothing` を返します。

## 引数

  * `ed`:       厳密対角化ソルバーオブジェクト。
  * `indices`:  消滅演算子の複合インデックス（`ed.full_hs.soi` の一部である必要があります）。
  * `sp_index`: 初期サブスペースインデックス。
