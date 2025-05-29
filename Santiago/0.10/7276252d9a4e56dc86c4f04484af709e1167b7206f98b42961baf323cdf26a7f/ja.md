```julia
massflow(
    sys::Santiago.System,
    M_in::Dict{String, Dict{String, T<:Real}};
    MC,
    scale_reliability,
    rng
) -> Dict{Santiago.Tech, NamedArrays.NamedArray{Float64}}

```

システムの質量流量を計算します。オプションでモンテカルロ（MC）シミュレーションを使用できます。

## 引数:

  * `M_in`: 各ソースの各物質の流入を含む辞書。
  * `MC`: false の場合、ディリクレ分布の期待値が移転係数として使用されます。そうでない場合、移転係数はディリクレ分布からサンプリングされます。
  * `scale_reliability`: すべての `Techs` の `transC_reliability` をスケーリングするための係数。
  * `rng`: オプション、乱数生成器。これは、スレッドセーフを取得するためにマルチスレッド処理にのみ必要です。
