```
PropsSI(output::AbstractString, name1::AbstractString, value1::Real, name2::AbstractString, value2::Real, fluid::AbstractString)
```

状態に依存する値を返します。

> 純粋および擬似純粋な流体の場合、状態を固定するために2つの状態点が必要です。状態方程式はTとρを状態変数として基にしているため、T、ρは常に最も速い入力となります。P、Tは少し遅く（3-10倍）、その後Tやρが与えられない入力（p、hなど）が続きます。これらははるかに遅くなります。速度が問題であれば、TTSEやバイキュービック補間を使用したテーブルベースの補間方法を検討できます。


# 引数

  * `fluid::AbstractString`: CoolPropの一部である流体の名前、例えば「n-プロパン」。異なる流体タイプのリストを取得するには、`get_global_param_string(key)`を呼び出し、`key`を次のいずれかに設定します：`["FluidsList", "incompressible_list_pure", "incompressible_list_solution", "mixture_binary_pairs_list", "predefined_mixtures"]`。また、CoolPropのオンラインドキュメントに流体のリストがあります [List of Fluids](http://www.coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)
  * `output::AbstractString`: 評価するパラメータの名前。リストを見るには、`?CoolProp_parameters`と入力します。
  * `name1::AbstractString`: 最初の状態点のパラメータ名
  * `value1::Real`: 最初の状態点の値
  * `name2::AbstractString`: 2番目の状態点のパラメータ名
  * `value2::Real`: 2番目の状態点の値

# 例

```julia
julia> PropsSI("D", "T", 300, "P", 101325, "n-Butane")
2.4325863624814326
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::DEB") # 非圧縮性純粋
857.1454
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::LiBr[0.23]") # 非圧縮性質量ベースの二元混合物
1187.5438243617214
julia> PropsSI("D", "T", 300, "P", 101325, "INCOMP::ZM[0.23]") # 非圧縮性体積ベースの二元混合物
1028.7273860290911
julia> PropsSI("Dmass", "T", 300, "P", 101325, "R125[0.5]&R32[0.5]")
3.5413381483914512
julia> split(get_global_param_string("mixture_binary_pairs_list"), ', ')[1] # ランダムな二元ペア
"100-41-4&106-42-3"
julia> PropsSI("Dmass", "T", 300, "P", 101325, "100-41-4[0.5]&106-42-3[0.5]") # エチルベンゼン[0.5]&p-キシレン[0.5]
857.7381127561846
```

# 参照

CoolProp::PropsSI(const std::string &, const std::string &, double, const std::string &, double, const std::string&) ```
