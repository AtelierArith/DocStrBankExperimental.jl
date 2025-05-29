```
subset(vnv::VarNamedVector, vns::AbstractVector{<:VarName})
```

`vns`にある変数の値を含む新しい`VarNamedVector`を返します。

含める変数は`VarName`の`subsumes`関係によって決定されます。つまり、例えば`subset(vnv, [@varname(x)])`は`@varname(x.a[1])`のような変数を含むことになります。

`vnv`内の変数の順序を保持します。

# 例

```jldoctest varnamedvector-subset julia> using DynamicPPL: VarNamedVector, @varname, subset

julia> vnv = VarNamedVector(@varname(x) => [1.0, 2.0], @varname(y) => [3.0]);

julia> subset(vnv, [@varname(x)]) == VarNamedVector(@varname(x) => [1.0, 2.0]) true

julia> subset(vnv, [@varname(x[2])]) == VarNamedVector(@varname(x[2]) => [2.0]) true
```
