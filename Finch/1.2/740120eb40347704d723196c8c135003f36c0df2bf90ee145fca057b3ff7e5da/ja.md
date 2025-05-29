```
SparseIntervalLevel{[Ti=Int], [Left, Right]}(lvl, [dim])
```

SparseIntervalLevelは、完全に[`fill_value`](@ref)ではない同等のスライス`A[:, ..., :, i]`のランを表します。SparseRunListレベルとの主な違いは、SparseIntervalレベルが「単一」の非フィルランのみを保存することです。プログラムがSparseIntervalに複数（>=2）のランを書き込もうとするとエラーが発生します。

`Ti`は最後のテンソルインデックスの型です。`Left`と`Right`は、位置とエンドポイントを保存するために使用される配列の型です。

```jldoctest
julia> tensor_tree(Tensor(SparseInterval(Element(0)), [0, 10, 0]))
3-Tensor
└─ SparseInterval (0) [1:3]
   └─ [2:2]: 10

julia> x = Tensor(SparseInterval(Element(0)), 10);

julia> @finch begin for i = extent(3,6); x[~i] = 1 end end;

julia> tensor_tree(x)
10-Tensor
└─ SparseInterval (0) [1:10]
   └─ [3:6]: 1

```
