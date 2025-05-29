```
periodic = Periodic(period, asymmetry)
```

`Periodic`関数は`TimeCurve`構造体のカスタムコンストラクタです。三角周期で定期的に繰り返す時間間隔を定義することができます。非対称周期を再現するために非対称性の測定を含みます。

# 引数

  * `period`: (`::Real`, `[s]`, `=1.0`) 周期の持続時間
  * `asymmetry`: (`::Real`, `=0.5`) 時間的非対称性係数。0から1の間。

# 戻り値

  * `periodic`: (`::TimeCurve`) TimeCurve構造体

# 例

```julia-repl
julia> periodic = Periodic(period=1.0, asymmetry=0.2)
```

![Periodic](../assets/periodic.svg)
