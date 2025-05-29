```
rv_to_kepler(r_i::AbstractVector{T1}, v_i::AbstractVector{T2}, t::T3 = 0) where {T1<:Number, T2<:Number, T3<:Number} -> KeplerianElements{Tepoch, T}
```

直交座標表現（位置ベクトル `r_i` [m] と速度ベクトル `v_i` [m / s]）をケプラー要素に変換します。オプションで、ユーザーは返される要素のエポックをパラメータ `t` を使用して指定できます。省略した場合、デフォルトは0になります。

!!! note
    出力型 `Tepoch` は `T3` を浮動小数点に変換することで得られ、出力型 `T` は `T1` と `T2` を昇格させ、その結果を浮動小数点に変換することで得られます。


# Returns

  * `KeplerianElements{Tepoch, T}`: ケプラー要素 [SI単位]。

# Remarks

アルゴリズムは**[1]**から適応されました。

特別なケースは次のように扱われます：

  * **円軌道かつ赤道面**: 昇交ノードの赤経と近点引数は0に設定されます。したがって、真異常は真経度に等しくなります。
  * **楕円軌道かつ赤道面**: 昇交ノードの赤経は0に設定されます。したがって、近点引数は近点の経度に等しくなります。
  * **円軌道かつ傾斜**: 近点引数は0に設定されます。したがって、真異常は緯度の引数に等しくなります。

# References

  * **[1]**: Schwarz, R (2014). Memorandum No. 2: Cartesian State Vectors to Keplerian Orbit   Elements. Available at www.rene-schwarz.com.
