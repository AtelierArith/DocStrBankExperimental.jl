```
SparseListLevel{[Ti=Int], [Ptr, Idx]}(lvl, [dim])
```

スパースレベルのサブファイバーは、完全に [`fill_value`](@ref) であるスライス `A[:, ..., :, i]` を表す必要はありません。代わりに、潜在的に非フィルスライスのみが `lvl` にサブファイバーとして保存されます。保存されているスライスを記録するためにソートされたリストが使用されます。オプションで、`dim` は最後の次元のサイズです。

`Ti` は最後のテンソルインデックスの型であり、`Tp` はレベル内の位置に使用される型です。`Ptr` と `Idx` は、位置とインデックスを保存するために使用される配列の型です。

```jldoctest
julia> tensor_tree(Tensor(Dense(SparseList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparseList (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   ├─ [:, 2]: SparseList (0.0) [1:3]
   └─ [:, 3]: SparseList (0.0) [1:3]
      ├─ [1]: 20.0
      └─ [3]: 40.0

julia> tensor_tree(Tensor(SparseList(SparseList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ SparseList (0.0) [:,1:3]
   ├─ [:, 1]: SparseList (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   └─ [:, 3]: SparseList (0.0) [1:3]
      ├─ [1]: 20.0
      └─ [3]: 40.0

```
