```
count_scalar_constants(tree::AbstractExpressionNode{T})::Int64 where {T}
```

ツリー内のスカラー定数の数をカウントします。定数配列を格納するためのベクターを事前に割り当てるために、get*scalar*constantsで使用されます。
