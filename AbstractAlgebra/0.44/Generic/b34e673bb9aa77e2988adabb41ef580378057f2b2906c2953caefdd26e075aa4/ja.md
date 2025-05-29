```
perm"..."
```

文字列マクロは、互いに素なサイクルを `Perm{Int}` に解析します。

GAP の出力用の文字列は、直接 `perm"..."` にコピーできます。長さ $1$ のサイクルは必要ありませんが、含めることができます。最小のサポートの置換が構築されます。すなわち、分解における最大の $n$ が親群 $S_n$ を決定します。

# 例

```jldoctest
julia> p = perm"(1,3)(2,4)"
(1,3)(2,4)

julia> typeof(p)
Perm{Int64}

julia> parent(p) == SymmetricGroup(4)
true

julia> p = perm"(1,3)(2,4)(10)"
(1,3)(2,4)

julia> parent(p) == SymmetricGroup(10)
true
```
