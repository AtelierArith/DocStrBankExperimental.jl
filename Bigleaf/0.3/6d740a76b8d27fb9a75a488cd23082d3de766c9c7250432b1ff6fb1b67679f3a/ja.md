```
stability_parameter(z,d,MOL)
stability_parameter(z,d,Tair, pressure, ustar, H; constants)
stability_parameter!(df::AbstractDataFrame; z,d, MOL=nothing, constants)

は、下層大気における成層を特徴づけるパラメータである安定性パラメータ「ゼータ」を計算します。

# 引数

  * `z`   : 高さ (m)
  * `d`   : ゼロ平面変位高さ (m)
  * `MOL` : モニン-オブコフ長 L (m)
  * `df`  : [`Monin_Obukhov_length`](@ref) に必要な変数を含む DataFrame

オプション

  * `constants=`[`BigleafConstants`](@ref)`()`

2番目のバリアントでは、DataFrame バリアントで `MOL=nothing` の場合、MOL は [`Monin_Obukhov_length`](@ref) によって計算されます。

# 詳細

安定性パラメータ $\zeta$ は次のように与えられます：

$\zeta = (z - d) / L$

ここで L はモニン-オブコフ長 (m) であり、[`Monin_Obukhov_length`](@ref) によって計算されます。変位高さは、関数 [`roughness_parameters`](@ref) から推定できます。

# 値

$\zeta$: 安定性パラメータ (-)。非変異 DataFrame バリアントはベクトルを返します。変異バリアントは列 [`:zeta`] を修正または追加します。

```

jldoctest; output = false using DataFrames df = DataFrame(Tair=25.0, pressure=100.0, ustar=0.2:0.1:1.0, H=40:20.0:200) z=40;d=15 zeta = stability_parameter.(z,d, df.Tair, df.pressure, df.ustar, df.H) all(zeta .< 0)

# output

true ```
