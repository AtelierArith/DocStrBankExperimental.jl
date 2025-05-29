```
cellrows(cols::VecColumnTable, refrows::IdDict)
```

[`findcell`](@ref)によって返されるオブジェクト`refrows`を処理するためのユーティリティ関数です。`refrows`のキーに対応する`cols`からのユニークな行値が辞書順にソートされ、新しい`VecColumnTable`の行として格納されます。`refrows`の値からの行インデックスのグループが行値の順序に合わせて置換され、`Vector`に収集されます。

# 戻り値

  * `cells::VecColumnTable`: `cols`の列からのユニークな行値。
  * `rows::Vector{Vector{Int}}`: 各組み合わせの行インデックス。
