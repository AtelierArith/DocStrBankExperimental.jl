```
mean_to_eccentric_anomaly(e::T1, M::T2; max_iterations::Integer = 10, tol::Union{Nothing, Number} = nothing) where {T1, T2} -> T
```

軌道の離心率 `e` と平均異常 `M` [rad] に基づいて、離心異常 (0, 2π) [rad] を計算します。

この関数は、ケプラーの方程式を解くためにニュートン-ラフソン法を使用します。

!!! note
    出力型 `T` は、`T1` と `T2` を浮動小数点数に昇格させることによって得られます。


# キーワード

  * `tol::Union{Nothing, Number}`: ニュートン-ラフソン法からの解を受け入れるための許容誤差。`tol` が `nothing` の場合、`eps(T)` になります。   (**デフォルト** = `nothing`)
  * `max_iterations::Number`: ニュートン-ラフソン法に許可される最大反復回数。1未満の場合は10に設定されます。   (**デフォルト** = 10)
