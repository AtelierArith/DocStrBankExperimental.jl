```
MultichannelComponent <: AbstractComponent
```

`AbstractComponent`を複数の「チャネル」に`projection`ベクトルを介して投影します。

オプションで、投影前にソースに`noise`を追加できます。デフォルトでは、`projection`の次のいずれかのオプションを使用して`MultichannelComponent`を構築できます。

  * `projection::AbstractVector`: カスタム投影ベクトルを直接渡します。
  * `projection::Pair{<:AbstractHeadmodel,String}`: 使用するヘッドモデルとアクティブにするソースを指定して投影ベクトルを生成します。

# フィールド

  * `component::AbstractComponent`: センサーに投影されるべきコンポーネント。
  * `projection::AbstractVector`または`projection::Pair{<:AbstractHeadmodel,String}`: (ソース)コンポーネント`c[t]`（ここで`t`は時間）をセンサー`s`に投影するベクトル`p`。`p`の長さはセンサーの数`s`に等しいです。通常、リードフィールド行列のスライスです。`out[s,t] = p[s]*c[t]`。
  * `noise::AbstractNoise`（オプション）: ソース空間に追加されるノイズ。デフォルトは`NoNoise`です。

# 例

```julia-repl
# バリアント 1: 投影ベクトルを手動で指定
julia> c1 = LinearModelComponent(; basis = p100(), formula = @formula(0 ~ 1), β = [1]);

julia> mc1 = UnfoldSim.MultichannelComponent(c, [1, 2, -1, 3, 5, 2.3, 1])
MultichannelComponent
  component: LinearModelComponent
  projection: Array{Float64}((7,)) [1.0, 2.0, -1.0, 3.0, 5.0, 2.3, 1.0]
  noise: NoNoise NoNoise()

# バリアント 2: ヘッドモデルを使用し、ソースを指定
julia> c2 = LinearModelComponent(; basis = p300(), formula = @formula(0 ~ 1), β = [1]);

julia> hart = headmodel(type = "hartmut");
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> mc2 = UnfoldSim.MultichannelComponent(c2, hart => "Right Occipital Pole")
MultichannelComponent
  component: LinearModelComponent
  projection: Array{Float64}((227,)) [-0.03461859471337842, -0.04321094803502425, 0.0037088347968313525, -0.014722528968861278, -0.0234889834534478, 0.02731807504242923, 0.038863688452528036, 0.1190531258070562, -0.09956890221613562, -0.0867729334438599  …  0.37435404409695094, -0.020863789022627935, 0.25627478723535513, -0.05777985212119245, 0.37104376432271147, -0.19446620423767172, 0.2590764703721097, -0.12923837607416555, 0.1732886690359311, 0.4703016561960567]
  noise: NoNoise NoNoise()
```

[`LinearModelComponent`](@ref)や[`MixedModelComponent`](@ref)も参照してください。
