```julia
cdag_connection(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}},
    sp_index::Int64
) -> Union{Nothing, Int64}

```

生成演算子からのサブスペース間接続を抽出します。Exact Diagonalizationソルバーから生成されます。接続が存在しない場合は`nothing`を返します。

## 引数

  * `ed`:       Exact Diagonalizationソルバーオブジェクト。
  * `indices`: 生成演算子の複合インデックス（`ed.full_hs.soi`の一部である必要があります）。
  * `sp_index`: 初期サブスペースインデックス。
