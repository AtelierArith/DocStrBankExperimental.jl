```
tanhtrans(trcsq,ntf)
```

大きさの二乗コヒーレンスの逆変換

...

# 引数

  * `trcsq::Float64`: 変換された二乗コヒーレンス
  * `ntf::Int64`: コヒーレンスを計算するために使用されるテーパーの数

...

...

# 出力

  * 出力は逆変換されたMSCを示す`Float64`です

...

# 例

変換されたコヒーレンスが7.3で自由度が6の場合、有意性は

```julia-repl
julia> invmscsig(tanhtrans(7.3,6),6)
```

有意性が0.9で自由度が6の場合、変換されたMSCは

```julia-repl
julia> atanhtrans(sqrt(mscsig(0.9,6)),6)
```

参照: [`multispec`](@ref) ```
