```
AbstractState_factory(backend::AbstractString, fluids::AbstractString)
```

AbstractStateインスタンスを生成し、他の低レベルアクセサ関数で使用するために生成された状態クラスへの整数ハンドルを返します。

# 引数

  * `backend`: 使用するバックエンドは次のいずれかです: `["HEOS", "REFPROP", "INCOMP", "IF97", "TREND", "HEOS&TTSE", "HEOS&BICUBIC", "SRK", "PR", "VTPR"]` など。
  * `fluids`: '&' で区切られた流体のリスト。可能な値のリストを取得するには、`get_global_param_string(key)`を呼び出し、`key`には次のいずれかを指定します: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`。また、CoolPropのオンラインドキュメントにある[流体のリスト](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)を参照するか、単に`?CoolProp_fluids`と入力してください。

# 例

```julia
julia> HEOS = AbstractState_factory("HEOS", "R245fa");
julia> TTSE = AbstractState_factory("HEOS&TTSE", "R245fa");
julia> BICU = AbstractState_factory("HEOS&BICUBIC", "R245fa");
julia> SRK = AbstractState_factory("SRK", "R245fa");
julia> PR = AbstractState_factory("PR", "R245fa");
```
