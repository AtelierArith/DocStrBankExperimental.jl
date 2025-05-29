```
foldup(node::DAG, 
    f_leaf::Function, 
    f_inner::Function, 
    ::Type{T})::T where {T}
```

グラフ上で下から上に関数を計算します。`f_leaf`は葉ノードで呼び出され、`f_inner`は内部ノードで呼び出されます。型`T`の値は回路を上に渡され、子ノードに対する関数として`f_inner`に渡されます。
