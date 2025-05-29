```
diff(t::T) where T <: AbstractTensor -> Linear{T}
```

テンソル `t` の微分を返します。各テンソル因子を一度に微分し、成分の次数に応じて符号を加えます。係数の型は通常 `DefaultCoefftype` です。ただし、テンソル成分の次数が整数でない場合、符号を考慮できるように係数の型が選択されます。

詳細は [`diff`](@ref)、[`LinearCombinations.DefaultCoefftype`](@ref) を参照してください。

# 例

通常、文字列の次数はその長さです。

```jldoctest
julia> import LinearCombinations: deg, diff

julia> deg(x::String) = length(x);

julia> function diff(x::String)
           if isempty(x) || x[1] == 'D'
               zero(Linear1{String,Int})
           else
               Linear1('D'*x => 1)end
       end;

julia> dx = diff("x")
Linear1{String, Int64} with 1 term:
"Dx"

julia> diff(dx)
Linear1{String, Int64} with 0 terms:
0

julia> t = Tensor("a", "bb", "ccc")
"a"⊗"bb"⊗"ccc"

julia> diff(t)
Linear{Tensor{Tuple{String, String, String}}, Int64} with 3 terms:
-"a"⊗"bb"⊗"Dccc"-"a"⊗"Dbb"⊗"ccc"+"Da"⊗"bb"⊗"ccc"
```
