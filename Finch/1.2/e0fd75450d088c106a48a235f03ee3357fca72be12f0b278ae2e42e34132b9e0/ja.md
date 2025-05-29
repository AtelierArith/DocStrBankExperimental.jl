```
SparseByteMapLevel{[Ti=Int], [Ptr, Tbl]}(lvl, [dims])
```

[`SparseListLevel`](@ref) と同様ですが、どのスライスが保存されているかをエンコードするために密なビットマップが使用されます。これにより、ByteMapレベルはランダムアクセスをサポートします。

`Ti` は最後のテンソルインデックスの型であり、`Tp` はレベル内の位置に使用される型です。

```jldoctest
julia> tensor_tree(Tensor(Dense(SparseByteMap(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparseByteMap (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   ├─ [:, 2]: SparseByteMap (0.0) [1:3]
   └─ [:, 3]: SparseByteMap (0.0) [1:3]
      ├─ [1]: 0.0
      └─ [3]: 0.0

julia> tensor_tree(Tensor(SparseByteMap(SparseByteMap(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ SparseByteMap (0.0) [:,1:3]
   ├─ [:, 1]: SparseByteMap (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   └─ [:, 3]: SparseByteMap (0.0) [1:3]
```
