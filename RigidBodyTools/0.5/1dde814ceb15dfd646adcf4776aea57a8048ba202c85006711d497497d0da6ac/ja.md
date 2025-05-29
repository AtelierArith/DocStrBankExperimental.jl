```
parent_to_child_transform(q::AbstractVector,joint::Joint)
```

`q`の関節の自由度エントリを使用して、関節`joint`の親から関節`joint`の子への変換演算子を作成します。`q`のエントリの数は、関節`joint`のタイプに適切でなければなりません。
