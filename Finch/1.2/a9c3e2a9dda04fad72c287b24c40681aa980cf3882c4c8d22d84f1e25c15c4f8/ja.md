```
DenseLevel{[Ti=Int]}(lvl, [dim])
```

密なレベルのサブファイバーは、各スライス `A[:, ..., :, i]` を `lvl` の異なるサブファイバーとして格納する配列です。オプションで、`dim` は最後の次元のサイズです。`Ti` はレベルをインデックス付けするために使用されるインデックスの型です。

```jldoctest
julia> ndims(Tensor(Dense(Element(0.0))))
1

julia> ndims(Tensor(Dense(Dense(Element(0.0)))))
2

julia> tensor_tree(Tensor(Dense(Dense(Element(0.0))), [1 2; 3 4]))
2×2-Tensor
└─ Dense [:,1:2]
   ├─ [:, 1]: Dense [1:2]
   │  ├─ [1]: 1.0
   │  └─ [2]: 3.0
   └─ [:, 2]: Dense [1:2]
      ├─ [1]: 2.0
      └─ [2]: 4.0
```
