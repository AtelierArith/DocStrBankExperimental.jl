```
SeisGain(d ; <キーワード引数>)
```

トレースのグループを取得します。入力と出力は2Dです。

# 引数

  * `d::Array{Real,2}`: 二次元データ。

# キーワード引数

  * `dt::Real=0.004`: サンプリング間隔（秒）。
  * `kind::AbstractString="time"`: kind="time" の場合、gain = t.^a . * exp(-bt); kind="agc" の場合、自動ゲイン制御が適用されます。
  * `coef::Vector{Real}=[2.0,0.0]`: kind="time" の場合、coef = [a,b]; kind="agc" の場合、coef = [agc_gate]
  * `normal::Int=0`: `normal=0` は正規化なし; `normal=1` は各トレースを振幅で正規化; `normal=2` は各トレースを rms 値で正規化/

# 例

```julia
julia> using PyPlot
julia> d = SeisHypEvents();
       dout = SeisGain(d, kind="agc", coef=[0.05]);
       SeisPlotTX([d dout]);
```

クレジット:  アーロン・ステイトン 更新: フアン・I・サビオーネ、マウリシオ・D・サッキ、フェルナンダ・カロッツィ
