```
immediatesubmodels(m::AbstractModel)
```

即時の子モデルのリストを返します。注意: モデルがリーフモデルの場合、返されるリストは空になります。

# 例

```julia-repl
julia> using SoleLogics

julia> branch = Branch(SoleLogics.parseformula("p∧q∨r"), "YES", "NO");

julia> immediatesubmodels(branch)
2-element Vector{SoleModels.ConstantModel{String}}:
 SoleModels.ConstantModel{String}
YES

 SoleModels.ConstantModel{String}
NO

julia> branch2 = Branch(SoleLogics.parseformula("s→p"), branch, 42);


julia> printmodel.(immediatesubmodels(branch2));
Branch
┐ p ∧ (q ∨ r)
├ ✔ YES
└ ✘ NO

ConstantModel
42
```

他にも [`submodels`](@ref), [`LeafModel`](@ref), [`AbstractModel`](@ref) を参照してください。
