```
har_forecast(x::Array, h::Int; flag::Bool = false, m::Array=[1,5,22])
```

HARモデルをフィッティングし、再帰的に予測することによって時系列の予測を計算します。

# 引数

  * `x::Array`: 時系列。
  * `h::Int`: 予測する期間の数。

# 出力

  * `xfor::Array`: 時系列の予測。最初の T-max(m) 要素は元の時系列です。

# オプション引数

  * `flag::Bool`: trueの場合、出力は行列で、最初の列が予測、2列目が下側信頼帯、3列目が上側信頼帯です。デフォルトはfalseです。
  * `m::Array`: HARモデルに含めるラグ。デフォルトは [1,5,22] です。

# 例

```julia
julia> har_forecast(fi_gen(100,0.2), 10)
```
