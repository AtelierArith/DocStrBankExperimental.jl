```
j4!(j4d::J4Propagator{Tepoch, T}, t::Number) where {Tepoch<:Number, T<:Number} -> SVector{3, T}, SVector{3, T}
```

`j4d`で定義された軌道を`t` [s]まで伝播させます（入力された平均要素のエポックの後）。 

!!! note
    `j4d`内の内部値は変更されます。


# 戻り値

  * `SVector{3, T}`: 伝播瞬間における慣性系で表された位置ベクトル [m]。
  * `SVector{3, T}`: 伝播瞬間における慣性系で表された速度ベクトル [m / s]。

# 備考

出力が表される慣性系は、軌道パラメータを生成するために使用された系に依存します。摂動理論は真の赤道を持つ慣性系を必要とすることに注意してください。
