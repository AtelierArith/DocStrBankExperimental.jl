```
get_circuit(hex_param::HeavyHexParameters, noise_param::AbstractNoiseParameters; kwargs...)
```

指定された回路およびノイズパラメータによってパラメータ化された[`Circuit`](@ref)オブジェクトの形で、ヘビーヘックスコードのシンドローム抽出回路を返します。

# 引数

  * `hex_param::HeavyHexParameters`: ヘビーヘックスコードのパラメータ。
  * `noise_param::AbstractNoiseParameters`: 回路のノイズパラメータ。

# キーワード引数

  * `noisy_prep::Bool = false`: 準備をノイズのあるものとして扱い、関連するノイズを特定するかどうか。デフォルトは`false`。`noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `noisy_meas::Bool = true`: 測定をノイズのあるものとして扱い、関連するノイズを特定するかどうか。デフォルトは`true`。`noisy_prep`と`noisy_meas`の両方が`true`の場合、フルランクデザインは生成できません。
  * `combined::Bool = haskey(noise_param.params, :combined) ? noise_param.params[:combined] : false,`: パウリX、Y、Z基底のSPAMノイズを同じものとして扱うかどうか。
  * `strict::Bool = false`: 相対精度に対して推定可能と見なすゲートについて厳密であるかどうか。
