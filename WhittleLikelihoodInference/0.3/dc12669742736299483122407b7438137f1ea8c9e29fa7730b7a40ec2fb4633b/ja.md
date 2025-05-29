```
WhittleLikelihood(model::Type{<:TimeSeriesModel}, ts, Δ; lowerΩcutoff, upperΩcutoff, taper)
WhittleLikelihood(model::Type{<:TimeSeriesModel}, timeseries::TimeSeries; lowerΩcutoff, upperΩcutoff, taper)
```

Whittle尤度、その勾配とヘッセ行列を評価する関数を生成します。

メモリを適切に事前割り当てする呼び出し可能な構造体を作成します。

```
(f::WhittleLikelihood)(θ)
```

θでWhittle尤度を評価します。

```
(f::WhittleLikelihood)(F,G,H,θ)
```

θでWhittle尤度を評価し、勾配とヘッセ行列をそれぞれGとHに格納します。F、G、またはHがnothingの場合、関数、勾配、またはヘッセ行列はそれぞれ評価されません。

# 引数

  * `model`: プロセスのモデル。TimeSeriesModel型である必要があります。したがって、`OU`であり、`OU(1,1)`ではありません。
  * `ts`: n by d行列の形の時系列（dは時系列モデルの次元）。
  * `Δ`: 時系列のサンプリングレート。
  * `timeseries`: `ts`と`Δ`の代わりに提供できます。`TimeSeries`型である必要があります。
  * `lowerΩcutoff`: 尤度に含まれる周波数範囲の下限。
  * `upperΩcutoff`: 尤度に含まれる周波数範囲の上限。
  * `taper`: オプションのテーパーで、`size(ts,1)`の長さのベクトルである必要があります。何も指定しない場合はテーパーは使用されません。

勾配を使用するには、モデルに`grad_add_sdf!`が指定されている必要があります。同様に、ヘッセ行列を使用するには、モデルに`hess_add_sdf!`が指定されている必要があります。

# 例

```julia-repl
julia> obj = WhittleLikelihood(OU, ones(1000), 1)
Whittle尤度はOUモデルのためのものです。

julia> obj([1.0, 1.0])
-2006.7870804551364

julia> F, G, H = 0.0, zeros(2), zeros(2,2)
(0.0, [0.0, 0.0], [0.0 0.0; 0.0 0.0])

julia> obj(F, G, H, [1.0, 1.0])
-2006.7870804551364

julia> G
2-element Vector{Float64}:
   2.777354965282642
 -17.45063591068618

julia> H
2×2 Matrix{Float64}:
 -0.00967179   0.0607696
  0.0607696   -0.381827
```
