```
gaussbeam(fwhm::T, lmax::Int; pol=false) where T
```

ガウスビームウィンドウ関数 $B_{\ell}$ を、ビームのFWHMをラジアンで与えた場合に計算します。ここで、$C_{\ell, \mathrm{measured}} = B_{\ell}^2 C_{\ell}$ です。このビームは、$\sigma^2 \ll 0$ の制限で有効であり、これはすべての高解像度CMB実験に該当します。

# 引数

  * `fwhm::T`: ガウスビームのFWHM（全幅半最大）をラジアンで指定
  * `lmax::Int`: 最大多極ℓ
  * `pol=false`: falseの場合、強度のためのスピン-0ビームを返します。trueの場合、スピン-2ビームを返します

# 戻り値

  * $$
    B_{\ell}
    $$

    を含む `Array{T,1}`。最初の要素は ℓ=0 を指します。

```
