```
namesingroup(chains::Chains, sym::Union{AbstractString,Symbol}; index_type::Symbol=:bracket)
```

同じ名前 `sym` のパラメータを返しますが、異なるインデックスを持ちます。デフォルトでは、ブラケットインデックス形式 `:sym[index]` が想定されています。ドットインデックスを持つパラメータには `index_type=:dot` を使用します。すなわち、`:sym.index` です。

チェーンに名前 `:sym` のパラメータが含まれている場合、それも返されます。

# 例

```jldoctest
julia> chn = Chains(rand(100, 2, 2), ["A[1]", "A[2]"]);

julia> namesingroup(chn, :A)
2-element Vector{Symbol}:
 Symbol("A[1]")
 Symbol("A[2]")

julia> # 特定の要素にも対応しています。
       namesingroup(chn, Symbol("A[1]"))
1-element Vector{Symbol}:
 Symbol("A[1]")

```

```jldoctest
julia> chn = Chains(rand(100, 3, 2), ["A.1", "A.2", "B"]);

julia> namesingroup(chn, :A; index_type=:dot)
2-element Vector{Symbol}:
 Symbol("A.1")
 Symbol("A.2")
```
