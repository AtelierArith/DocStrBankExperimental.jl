```
VarList_vvector(Vector{Vector{VariableReaction}}::vars; components=false) -> VarList_vvector
```

`VariableReaction`のベクトルのベクトルを説明する`VarList_vvector`を作成します。次に、`create_accessors`はデータ配列のベクトルのベクトルを返します。

`components = true`の場合、各ベクトルのベクトルの要素はデータ配列コンポーネントのベクトルになります。
