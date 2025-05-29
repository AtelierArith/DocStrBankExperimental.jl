```
regular_coulomb(ℓ,η,ρ)
```

正則クーロン波動関数 ℓ は次数（非負整数）、η は電荷（実数パラメータ）、ρ は半径座標（非負実変数）です。

次の値 F_ℓ(η,ρ) を返します。

$$
    F_\ell(\eta,\rho) = \frac{\rho^{\ell+1}2^\ell e^{i\rho-(\pi\eta/2)}}{|\Gamma(\ell+1+i\eta)|} \int_0^1 e^{-2i\rho t}t^{\ell+i\eta}(1-t)^{\ell-i\eta} \, dt
$$
