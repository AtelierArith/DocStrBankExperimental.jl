```
SeisEnvelope(in; <キーワード引数>)
```

入力トレースのグループのエンベロープ属性を計算します。

# 引数

  * `in`: 入力データ。最初の次元が時間の2D配列です。

# 例

```julia
julia> using PyPlot
julia> dtsec = 0.002; w = Ricker(dt=dtsec);
julia> e = SeisEnvelope(w); t=dtsec*collect(0:1:length(w)-1);plot(t,w,t,e,"-r");xlabel("時間 [s]")
```

*クレジット: Aaron Stanton,2017*
