```
SparsePointLevel{[Ti=Int], [Idx]}(lvl, [dim])
```

SparsePointレベルのサブファイバーは、完全に[`fill_value`](@ref)であるスライス`A[:, ..., :, i]`を表す必要はありません。代わりに、潜在的に非フィルスライスのみが`lvl`のサブファイバーとして保存されます。SparseListレベルとの主な違いは、SparsePointレベルが「単一」の非フィルスライスのみを保存することです。プログラムがSparsePointに複数（>=2）の座標を書き込もうとするとエラーが発生します。

`Ti`は最後のテンソルインデックスの型です。`Ptr`と`Idx`は、位置とインデックスを保存するために使用される配列の型です。

```jldoctest
julia> tensor_tree(Tensor(Dense(SparsePoint(Element(0.0))), [10 0 0; 0 20 0; 0 0 30]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparsePoint (0.0) [1:3]
   │  └─ [1]: 10.0
   ├─ [:, 2]: SparsePoint (0.0) [1:3]
   │  └─ [2]: 20.0
   └─ [:, 3]: SparsePoint (0.0) [1:3]
      └─ [3]: 30.0

julia> tensor_tree(Tensor(SparsePoint(Dense(Element(0.0))), [0 0 0; 0 0 30; 0 0 30]))
3×3-Tensor
└─ SparsePoint (0.0) [:,1:3]
   └─ [:, 3]: Dense [1:3]
      ├─ [1]: 0.0
      ├─ [2]: 30.0
      └─ [3]: 30.0

```
