```
lift(a::T) where {T <: Zmod_fmpz_mat}
```

行列 $a$ を $\mathbb{Z}$ 上の行列に持ち上げるリフトを返します。すなわち、返される行列のエントリは、$a$ のエントリを $\mathbb{Z}$ に持ち上げたものです。
