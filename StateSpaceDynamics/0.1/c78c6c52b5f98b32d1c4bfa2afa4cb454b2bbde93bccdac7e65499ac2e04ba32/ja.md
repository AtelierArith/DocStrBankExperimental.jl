```
block_tridiagonal_inverse(A, B, C)
```

ブロックトリディアゴナル行列の逆行列を計算します。

# 引数

  * `A`: 下対角ブロック。
  * `B`: 主対角ブロック。
  * `C`: 上対角ブロック。

# 戻り値

  * `λii`: 逆行列の対角ブロック。
  * `λij`: 逆行列の非対角ブロック。

# 注: この実装は次の論文からのものです：

"An Accelerated Lambda Iteration Method for Multilevel Radiative Transfer” Rybicki, G.B., and Hummer, D.G., Astronomy and Astrophysics, 245, 171–181 (1991), Appendix B.
