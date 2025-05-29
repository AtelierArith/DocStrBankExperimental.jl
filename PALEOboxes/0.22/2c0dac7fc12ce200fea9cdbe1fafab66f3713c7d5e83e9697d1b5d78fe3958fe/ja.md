```
VarList_namedtuple(varcollection; components=false) -> VarList_namedtuple
```

`VariableReaction`のコレクションを説明する`VarList_namedtuple`を作成します。`create_accessors`は、フィールド名が`VariableReaction.localname`で、フィールド値が対応するデータ配列のNamedTupleを返します。

`components = true`の場合、各NamedTupleフィールドはデータ配列コンポーネントのベクターになります。
