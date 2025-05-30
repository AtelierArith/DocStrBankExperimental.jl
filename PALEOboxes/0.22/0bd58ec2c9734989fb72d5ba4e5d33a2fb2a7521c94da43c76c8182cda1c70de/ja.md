```
VarList_tuple(varcollection; components=false) -> VarList_tuple
```

`VariableReaction`のコレクションを記述する`VarList_tuple`を作成します。`create_accessors`は、データ配列のタプルを返します。

`varcollection`のエントリに`nothing`があると、反応メソッドに供給される配列のタプルの対応するエントリに`nothing`が生成されます。

`components = true`の場合、各タプルフィールドはデータ配列コンポーネントのベクターになります。
