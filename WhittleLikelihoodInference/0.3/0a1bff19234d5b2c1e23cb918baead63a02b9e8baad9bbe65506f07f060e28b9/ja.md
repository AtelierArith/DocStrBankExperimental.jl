```
DebiasedWhittleLikelihood(model::Type{<:TimeSeriesModel}, ts, Δ; lowerΩcutoff, upperΩcutoff, taper)
DebiasedWhittleLikelihood(model::Type{<:TimeSeriesModel}, timeseries::TimeSeries; lowerΩcutoff, upperΩcutoff, taper)
```

デビアス・ウィトル尤度を評価し、その勾配と期待ヘッセ行列を計算する関数を生成します。

メモリを適切に事前割り当てする呼び出し可能な構造体を作成します。

```
(f::DebiasedWhittleLikelihood)(θ)
```

θでウィトル尤度を評価します。

```
(f::DebiasedWhittleLikelihood)(F,G,EH,θ)
```

θでウィトル尤度を評価し、勾配をGに、期待ヘッセ行列をEHにそれぞれ格納します。F、G、またはEHがnothingの場合、それぞれ関数、勾配、または期待ヘッセ行列は評価されません。

# 引数

  * `model`: プロセスのモデル。TimeSeriesModel型である必要があります。したがって、`OU`であり、`OU(1,1)`ではありません。
  * `ts`: n by d行列の形の時系列（dは時系列モデルの次元）です。
  * `Δ`: 時系列のサンプリングレートです。
  * `timeseries`: `ts`と`Δ`の代わりに提供できます。`TimeSeries`型である必要があります。
  * `lowerΩcutoff`: 尤度に含まれる周波数範囲の下限です。
  * `upperΩcutoff`: 尤度に含まれる周波数範囲の上限です。
  * `taper`: オプションのテーパーで、`size(ts,1)`の長さのベクトルである必要があります。何も指定しない場合はテーパーは使用されません。

勾配を使用するには、モデルに`grad_add_sdf!`または`grad_acv!`が指定されている必要があります。同様に、ヘッセ行列を使用するには、モデルに`hess_add_sdf!`または`hess_acv!`が指定されている必要があります。

# 例

```julia-repl
julia> obj = DebiasedWhittleLikelihood(OU, ones(1000), 1)
Debiased Whittle likelihood for the OU model.

julia> obj([1.0, 1.0])
-1982.0676530999626

julia> F, G, EH = 0.0, zeros(2), zeros(2,2)
(0.0, [0.0, 0.0], [0.0 0.0; 0.0 0.0])

julia> obj(F, G, EH, [1.0, 1.0])
-1982.0676530999626

julia> G
2-element Vector{Float64}:
 1998.3136810970122
 -685.7904154568779

julia> H
2×2 Matrix{Float64}:
 -0.00967179   0.0607696
  0.0607696   -0.381827
```
