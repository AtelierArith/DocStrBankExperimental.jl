```
VarList_namedtuple_fields(objectwithvars; components=false) -> VarList_namedtuple
```

`objectwithvars`内の`VariableReaction`フィールドを説明する`VarList_namedtuple`を作成します。次に、`create_accessors`は、フィールド名 = `objectwithvars`内のフィールド名、フィールド値 = 対応するデータ配列のNamedTupleを返します。

`components = true`の場合、各NamedTupleフィールドはデータ配列コンポーネントのベクトルになります。
