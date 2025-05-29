```
imag_part(q::Quaternion{T}) -> NTuple{3, T}
```

クォータニオン `q` の虚部を返します。

この関数は、複素数に対して `Base.imag` が返す `Real` とは異なることに注意してください。

関連情報: [`real`](@ref), [`conj`](@ref).

# 例

```jldoctest
julia> imag_part(Quaternion(1,2,3,4))
(2, 3, 4)
```
