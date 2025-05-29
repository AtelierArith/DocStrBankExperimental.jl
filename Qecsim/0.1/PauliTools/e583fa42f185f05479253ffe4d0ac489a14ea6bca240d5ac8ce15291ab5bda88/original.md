```
bsp(
    A::AbstractVecOrMat{Bool}, B::AbstractVecOrMat{Bool}
) -> Union{Bool,BitVector,BitMatrix}
```

Return the binary symplectic product of `A` with `B`, given in binary symplectic form.

The binary symplectic product $⊙$ is defined as $A ⊙ B ≡ A Λ B \bmod 2$ where $Λ = \left[\begin{smallmatrix} 0 & I \\ I & 0 \end{smallmatrix}\right]$.

# Examples

```jldoctest
julia> a = BitVector([1, 0, 0, 0]);  # XI

julia> b = BitVector([0, 0, 1, 0]);  # ZI

julia> bsp(a', b)
true
```

```jldoctest
julia> stabilizers = BitMatrix(  # 5-qubit stabilizers
       [1 0 0 1 0 0 1 1 0 0     # XZZXI
        0 1 0 0 1 0 0 1 1 0     # IXZZX
        1 0 1 0 0 0 0 0 1 1     # XIXZZ
        0 1 0 1 0 1 0 0 0 1]);  # ZXIXZ

julia> error = BitVector([0, 0, 1, 1, 0, 0, 1, 0, 1, 0]);  # IZXYI

julia> bsp(stabilizers, error)
4-element BitVector:
 0
 1
 1
 0
```
