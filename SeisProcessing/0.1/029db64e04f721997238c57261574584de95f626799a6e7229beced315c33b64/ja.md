```
Berlage(; <keyword arguments>)
```

Berlageウェーブレットを作成します。

# 引数

  * `dt=0.002`: サンプリング間隔（秒）。
  * `f0=20.0`: 中心周波数（Hz）。
  * `m::Real=2`: Berlageウェーブレットの指数パラメータ。
  * `alpha::Real=180.0`: Berlageウェーブレットのアルファパラメータ（rad/秒）。
  * `phi0::Real`: 位相回転（ラジアン）。

# 例

```julia
julia> w = Berlage(); plot(w);
```

**参考文献**

  * Aldridge, David F., 1990, The berlage wavelet: GEOPHYSICS, 55, 1508–1511.
