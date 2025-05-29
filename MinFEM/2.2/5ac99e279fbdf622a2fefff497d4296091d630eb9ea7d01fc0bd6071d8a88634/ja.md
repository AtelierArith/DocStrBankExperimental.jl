```
evaluate_quadrature_function(
    mesh::Mesh,
    f::Function,
    region::Set{Domain};
    order::Int64 = 1, 
    qdim::Int64 = 1
) -> Vector{Float64}
```

以前の evaluate*quadrature*function(...) と同様ですが、関連する領域のために必須引数として `Set{Domain}` を受け取り、`Set{Int64}` を使用するキーワード引数を置き換えます。ドメインからノードを抽出し、それを基本関数に渡します。
