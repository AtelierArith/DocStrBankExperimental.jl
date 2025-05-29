```
joint_transform(q::AbstractVector,joint::Joint)
```

`q`の関節自由度エントリを使用して、関節変換演算子を作成します。`q`のエントリの数は、関節`joint`のタイプに適切でなければなりません。
