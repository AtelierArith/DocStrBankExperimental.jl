```
TBA{K}(H::Union{Formula, OperatorSet{<:Quadratic}, Generator{<:OperatorSet{<:Quadratic}}}, commutator::Union{AbstractMatrix, Nothing}=nothing) where {K<:TBAKind}
TBA{K}(lattice::Union{AbstractLattice, Nothing}, H::Union{Formula, OperatorSet{<:Quadratic}, Generator{<:OperatorSet{<:Quadratic}}}, commutator::Union{AbstractMatrix, Nothing}=nothing) where {K<:TBAKind}

TBA{K}(H::Union{OperatorSet{<:Operator}, Generator{<:OperatorSet{<:Operator}}}, q::Quadraticization, commutator::Union{AbstractMatrix, Nothing}=nothing) where {K<:TBAKind}
TBA{K}(lattice::Union{AbstractLattice, Nothing}, H::Union{OperatorSet{<:Operator}, Generator{<:OperatorSet{<:Operator}}}, q::Quadraticization, commutator::Union{AbstractMatrix, Nothing}=nothing) where {K<:TBAKind}

TBA(lattice::AbstractLattice, hilbert::Hilbert, terms::OneOrMore{Term}, boundary::Boundary=plain; neighbors::Union{Int, Neighbors}=nneighbor(terms))
TBA{K}(lattice::AbstractLattice, hilbert::Hilbert, terms::OneOrMore{Term}, boundary::Boundary=plain; neighbors::Union{Int, Neighbors}=nneighbor(terms)) where {K<:TBAKind}
```

Construct a tight-binding quantum lattice system.
