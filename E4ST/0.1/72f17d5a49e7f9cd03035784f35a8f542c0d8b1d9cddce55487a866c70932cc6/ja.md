```
promote_cols!(data)
```

データ内のすべてのテーブルの列を、すべての `Vector{AT}` に対して `Vector{CT}` に昇格させます。ここで、`AT` は抽象型であり、すべての要素は具体的な型 `CT` です。
