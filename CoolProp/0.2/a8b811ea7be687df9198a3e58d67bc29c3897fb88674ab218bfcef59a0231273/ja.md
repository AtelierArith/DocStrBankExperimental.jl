```
PropsSI(fluid::AbstractString, output::AbstractString)
```

熱力学状態に依存しない値を返します - これは、`PropsSI(output, "", 0, "", 0, fluid)`を呼び出す便利な関数です。

# 引数

  * `fluid::AbstractString`: CoolPropの一部である流体の名前、例えば「n-プロパン」。可能な値のリストを取得するには、`get_global_param_string(key)`を呼び出し、`key`を次のいずれかに設定します: `["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`。また、CoolPropのオンラインドキュメントにある[流体のリスト](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)を参照するか、単に`?CoolProp_fluids`と入力してください。
  * `output::AbstractString`: 評価するパラメータの名前。リストを表示するには`?CoolProp_parameters`を入力してください。

# 例

```julia
julia> PropsSI("n-ブタン", "rhomolar_critical")
3922.769612987809
```

# 参照

CoolProp::Props1SI(std::string, std::string)
