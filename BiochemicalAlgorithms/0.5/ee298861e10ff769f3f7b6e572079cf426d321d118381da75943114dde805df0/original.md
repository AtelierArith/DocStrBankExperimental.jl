```
TrivialAtomBijection{T} <: AbstractAtomBijection{T}
```

Bijection of atoms based on their order in the associated atom containers.

# Constructors

```julia
TrivialAtomBijection(A::AtomTable{T}, B::AtomTable{T})
```

Creates a new `TrivialAtomBijection{T}` from the given tables. Atom order is determined by row number.

```julia
TrivialAtomBijection(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
```

Creates a new `TrivialAtomBijection{T}` with the atoms of the individual atom containers.

```julia
TrivialAtomBijection(A::AtomTable{T}, B::AbstractAtomContainer{T})
```

Creates a new `TrivialAtomBijection{T}` by filtering `B` for atom numbers contained in `A`. Atom order after filtering must be the same as in `A`.
