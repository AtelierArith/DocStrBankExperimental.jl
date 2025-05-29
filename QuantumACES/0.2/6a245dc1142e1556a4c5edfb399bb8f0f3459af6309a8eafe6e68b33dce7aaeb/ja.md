```
get_circuit(rotated_param::RotatedPlanarParameters, noise_param::AbstractNoiseParameters; kwargs...)
```

回転平面符号のシンドローム抽出回路を、供給された回路およびノイズパラメータによってパラメータ化された[`Circuit`](@ref)オブジェクトの形で返します。

# 引数

  * `rotated_param::RotatedPlanarParameters`: 回転平面符号のためのパラメータ。
  * `noise_param::AbstractNoiseParameters`: 回路のためのノイズパラメータ。

# キーワード引数

  * `noisy_prep::Bool = false`: 準備をノイズのあるものとして扱い、関連するノイズを特定するかどうか。デフォルトは`false`。`noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `noisy_meas::Bool = true`: 測定をノイズのあるものとして扱い、関連するノイズを特定するかどうか。デフォルトは`true`。`noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `combined::Bool = haskey(noise_param.params, :combined) ? noise_param.params[:combined] : false,`: パウリX、Y、Z基底のSPAMノイズを同じものとして扱うかどうか。
  * `strict::Bool = false`: どのゲートが相対精度に対して推定可能と見なされるかについて厳密であるかどうか。
