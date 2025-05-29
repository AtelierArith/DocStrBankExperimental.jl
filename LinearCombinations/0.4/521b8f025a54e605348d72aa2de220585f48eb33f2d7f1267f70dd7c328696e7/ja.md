```
coprod(t::T) where T <: AbstractTensor -> Linear{Tensor{Tuple{T,T}}}
```

テンソルのコプロダクトを返します。これは、その成分のコプロダクトから計算されます。符号は通常の符号規則に従って導入されます。すべての次数が整数である場合、係数の型は `DefaultCoefftype` です。

この関数は線形です。

参照: [`coprod`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# 例

```jldoctest
julia> import LinearCombinations: deg, coprod

julia> deg(x::String) = length(x);

julia> coprod(x::String) = Linear(Tensor(x[1:k], x[k+1:end]) => 1 for k in 1:length(x)-1);

julia> coprod("abc")
Linear{Tensor{Tuple{String, String}}, Int64} with 2 terms:
"a"⊗"bc"+"ab"⊗"c"

julia> t = Tensor("abc", "xyz")
"abc"⊗"xyz"

julia> coprod(t)
Linear{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 4 terms:
("a"⊗"xy")⊗("bc"⊗"z")-("ab"⊗"x")⊗("c"⊗"yz")+("a"⊗"x")⊗("bc"⊗"yz")+("ab"⊗"xy")⊗("c"⊗"z")
```
