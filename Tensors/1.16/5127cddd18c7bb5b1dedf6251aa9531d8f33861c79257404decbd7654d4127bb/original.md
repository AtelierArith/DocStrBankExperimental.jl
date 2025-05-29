```
dcontract(::SecondOrderTensor, ::SecondOrderTensor)
dcontract(::SecondOrderTensor, ::FourthOrderTensor)
dcontract(::FourthOrderTensor, ::SecondOrderTensor)
dcontract(::FourthOrderTensor, ::FourthOrderTensor)
```

Compute the double contraction between two tensors. The symbol `⊡`, written `\boxdot`, is overloaded for double contraction. The reason `:` is not used is because it does not have the same precedence as multiplication.

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> B = rand(SymmetricTensor{2, 2});

julia> dcontract(A,B)
0.7654348606012742

julia> A ⊡ B
0.7654348606012742
```
