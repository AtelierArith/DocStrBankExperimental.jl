```
bsp(
    A::AbstractVecOrMat{Bool}, B::AbstractVecOrMat{Bool}
) -> Union{Bool,BitVector,BitMatrix}
```

`A`と`B`の二項対称積を、二項対称形式で返します。

二項対称積 $⊙$ は $A ⊙ B ≡ A Λ B \bmod 2$ と定義され、ここで $Λ = \left[\begin{smallmatrix} 0 & I \\ I & 0 \end{smallmatrix}\right]$ です。

# 例

```jldoctest
julia> a = BitVector([1, 0, 0, 0]);  # XI

julia> b = BitVector([0, 0, 1, 0]);  # ZI

julia> bsp(a', b)
true
```

```jldoctest
julia> stabilizers = BitMatrix(  # 5量子ビットの安定器
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
