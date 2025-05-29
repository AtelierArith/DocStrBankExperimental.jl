```
struct MacaulayNullspace{T,MT<:AbstractMatrix{T},BT}
    matrix::MT
    basis::BT
    accuracy::T
end
```

この行が `basis` にインデックス付けされた行を持つ行列は、`basis` にインデックス付けされた列を持つマカーレイ行列の右ヌル空間（または `basis` にインデックス付けされた行と列を持つモーメント行列の像空間）として解釈できます。`matrix[i, j]` の値は、ヌル空間（または像）空間の `j` 番目の生成子に対する `basis` の `i` 番目の要素の値として解釈されるべきです。
