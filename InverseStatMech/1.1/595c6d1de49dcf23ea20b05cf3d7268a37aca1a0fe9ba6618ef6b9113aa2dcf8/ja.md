```
ornstein_zernike_v(dim::Int, ρ::Float64, g2::Function, s::Function, closure::String, r_vec::AbstractVector = 0.025:0.05:10,
k_vec::AbstractVector = 0.025:0.05:20) :: Interpolations.GriddedInterpolation
```

オーンスタイン-ゼルニケポテンシャル ($βv(r)$) をオーンスタイン-ゼルニケ方程式を使用して計算します。

## 引数

  * `dim::Int`: システムの次元数。
  * `ρ::Real`: システムの粒子密度（単位体積あたりの粒子数）。
  * `g2::Function`: $r$ の関数としての対相関関数 $g_2(r)$。
  * `s::Function`: $k$ の関数としての構造因子 $S(k)$。
  * `closure::String`: オーンスタイン-ゼルニケ方程式で使用される閉じる関係。可能な値は次のとおりです：

      * "PMF": 平均力のポテンシャル、基本的に $-\ln(g_2(r))$。
      * "MFA": 平均場近似 (MFA)。
      * "HNC": ハイパーネッテッドチェーン閉じる。
      * "PY": パーカス-イェビック閉じる。

## オプション引数

  * `r_vec::AbstractVector`: g_2(r) 関数が有効な r 値のベクトル。デフォルトは 0.025:0.05:10。
  * `k_vec::AbstractVector`: S(k) 関数が有効な k 値のベクトル。デフォルトは 0.025:0.05:20。

## 戻り値

  * OZポテンシャル $βv(r)$ を表す `Interpolations.GriddedInterpolation` のインスタンスで、通常の関数として使用できます。

注意: `g2` および `s` 関数は、それぞれ r および k の関数として対相関関数と構造因子を返す有効な関数として提供する必要があります。

## 例：

```
function pair_correlation_function(r)
    # ここで対相関関数を定義します

    # ...
end
function structure_factor(k)
    # ここで構造因子を定義します

    # ...
end
closure_type = "PY"
oz_v = ornstein_zernike_v(3, 0.5, pair_correlation_function, structure_factor, closure_type)
```
