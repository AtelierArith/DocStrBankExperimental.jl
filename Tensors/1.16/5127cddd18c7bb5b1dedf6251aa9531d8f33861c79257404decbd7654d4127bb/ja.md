```
dcontract(::SecondOrderTensor, ::SecondOrderTensor)
dcontract(::SecondOrderTensor, ::FourthOrderTensor)
dcontract(::FourthOrderTensor, ::SecondOrderTensor)
dcontract(::FourthOrderTensor, ::FourthOrderTensor)
```

2つのテンソル間の二重収縮を計算します。記号 `⊡` は、二重収縮のためにオーバーロードされています。`:` が使用されない理由は、乗算と同じ優先順位を持たないからです。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> B = rand(SymmetricTensor{2, 2});

julia> dcontract(A,B)
0.7654348606012742

julia> A ⊡ B
0.7654348606012742
```
