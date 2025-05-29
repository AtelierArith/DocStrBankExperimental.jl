```
Flow{D::Int, T::Float, Sf<:AbstractArray{T,D}, Vf<:AbstractArray{T,D+1}, Tf<:AbstractArray{T,D+2}}
```

多次元浸漬境界流シミュレーションのための複合型。

Flowは、直交格子上で非定常非圧縮性の[ナビエ-ストークス方程式](https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_equations)を解きます。固体境界は[境界データ浸漬法](https://eprints.soton.ac.uk/369635/)を使用してモデル化されます。主な変数はスカラー圧力 `p`（次元 `D` の配列）と速度ベクトル場 `u`（次元 `D+1` の配列）です。
