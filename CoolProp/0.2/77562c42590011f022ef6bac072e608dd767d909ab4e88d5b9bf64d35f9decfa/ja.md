```
PhaseSI(name1::AbstractString, value1::Real, name2::AbstractString, value2::Real, fluid::AbstractString)
```

相の文字列表現を返します。有効な状態は次のとおりです: "liquid", "supercritical", "supercritical*gas", "supercritical*liquid", "critical_point", "gas", "twophase"

# 引数

  * `fluid::AbstractString`: CoolPropの一部である流体の名前、例えば "n-Propane"。異なる流体タイプのリストを取得するには、`get_global_param_string(key)`を呼び出し、`key`には次のいずれかを指定します: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`。また、CoolPropのオンラインドキュメントにリストがあります [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)
  * `name1::AbstractString`: 最初の状態点のパラメータ名
  * `value1::Real`: 最初の状態点の値
  * `name2::AbstractString`: 2番目の状態点のパラメータ名
  * `value2::Real`: 2番目の状態点の値

# 例

```julia
julia> PhaseSI("T", PropsSI("TCRIT", "Water"), "P", PropsSI("PCRIT", "Water"), "Water")
"critical_point"
julia> PhaseSI("T", 300, "Q", 1, "Water")
"twophase"
julia> PhaseSI("P", "T", 300, "Q", 1, "Water")
3536.806750422325
julia> PhaseSI("T", 300, "P", 3531, "Water")
"gas"
julia> PhaseSI("T", 300, "P", 3541, "Water")
"liquid"
```

# 参照

CoolProp::PhaseSI(const std::string &, double, const std::string &, double, const std::string&)
