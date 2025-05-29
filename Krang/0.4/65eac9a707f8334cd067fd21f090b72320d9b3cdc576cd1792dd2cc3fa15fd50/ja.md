```julia
Ir(pix::Krang.AbstractPixel, νr::Bool, rs) -> Any

```

$$
I_r=\int\frac{dr}{\sqrt{\mathcal{R(r)}}}
$$

の不定積分を返します。$\mathcal{R}(r)$の実装については[`r_potential(x)`](@ref)を参照してください。

# 引数

  * `pix`  : ピクセル情報
  * `νr` : 放出時の放射速度方向の符号。これはケース3およびケース4の測地線では常に正です。
  * `rs` : 放出半径
