量子オブジェクト（ケット、演算子、またはブラ）を数値でスケーリングする。

```jldoctest
julia> @ket k
|k⟩

julia> 2*k
2|k⟩

julia> @op A
A

julia> 2*A
2A
```
