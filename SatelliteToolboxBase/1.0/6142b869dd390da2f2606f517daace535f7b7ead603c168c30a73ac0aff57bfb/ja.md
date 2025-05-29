```
kepler_to_rv(ke::KeplerianElements{Tepoch, T}) where {Tepoch <: Number, T <: Number} -> SVector{3, T}, SVector{3, T}
```

ケプラー要素 `ke` を直交座標表現（位置ベクトル `r` [m] と速度ベクトル `v` [m / s]）に変換します。

!!! note
    返されるベクトルは、ケプラー要素と同じ参照フレームで表現されています。


# Returns

  * `SVector{3, T}`: 慣性参照フレームで表現された位置ベクトル [m]。
  * `SVector{3, T}`: 慣性参照フレームで表現された速度ベクトル [m]。

# Remarks

このアルゴリズムは **[1]** と **[2]**(p. 37-38) から適応されました。

# References

  * **[1]**: Schwarz, R (2014). Memorandum No. 2: Cartesian State Vectors to Keplerian Orbit   Elements. Available at www.rene-schwarz.com.
  * **[2]**: Kuga, H. K., Carrara, V., Rao, K. R (2005). Introdução à Mecânica Orbital. 2ª ed.   Instituto Nacional de Pesquisas Espaciais.
