```
SparseRunListLevel{[Ti=Int], [Ptr, Left, Right]}(lvl, [dim]; [merge = true])
```

SparseRunListLevelは、完全に[`fill_value`](@ref)ではない同等のスライス`A[:, ..., :, i]`のランを表します。ソートされたリストは、各ランの左端と右端の位置を記録するために使用されます。オプションで、`dim`は最後の次元のサイズです。

`Ti`は最後のテンソルインデックスの型であり、`Tp`はレベル内の位置に使用される型です。`Ptr`、`Left`、および`Right`は、位置と端点を格納するために使用される配列の型です。

`merge`キーワード引数は、レベルが重複する連続したランをマージするかどうかを指定するために使用されます。

```jldoctest
julia> tensor_tree(Tensor(Dense(SparseRunListLevel(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparseRunList (0.0) [1:3]
   │  ├─ [1:1]: 10.0
   │  └─ [2:2]: 30.0
   ├─ [:, 2]: SparseRunList (0.0) [1:3]
   └─ [:, 3]: SparseRunList (0.0) [1:3]
      ├─ [1:1]: 20.0
      └─ [3:3]: 40.0
```
