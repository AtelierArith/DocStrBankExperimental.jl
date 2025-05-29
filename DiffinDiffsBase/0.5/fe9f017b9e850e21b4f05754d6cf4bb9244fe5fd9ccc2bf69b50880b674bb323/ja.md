```
findcell(cols::VecColumnTable)
findcell(names, data, esample=Colon())
```

データ列のコレクションの行インデックスをグループ化し、これらの列からの行値の組み合わせが各グループ内で同じになるようにします。

関連する列の部分を直接[`VecColumnTable`](@ref)として提供する代わりに、`data`の列の`names`を指定することができます。これは、`esample`で示された選択された行に対して、任意の`Tables.jl`互換のテーブルタイプに対して行われます。`esample`が`data`のすべての行をカバーしない限り、行インデックスは`data`全体のものではなく、`esample`に基づいて選択されたサブサンプルのものになります。

# 戻り値

  * `IdDict{Tuple, Vector{Int}}`: ユニークな行値から行インデックスへのマップ。
