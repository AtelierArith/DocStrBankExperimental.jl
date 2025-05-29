```
regular_coulomb(ℓ,η,ρ)
```

Regular Coulomb wave function ℓ is the order(non-negative integer), η is the charge (real parameter) and ρ is the radial coordinate (non-negative real variable).

returns the value F_ℓ(η,ρ) given by 

$$
    F_\ell(\eta,\rho) = \frac{\rho^{\ell+1}2^\ell e^{i\rho-(\pi\eta/2)}}{|\Gamma(\ell+1+i\eta)|} \int_0^1 e^{-2i\rho t}t^{\ell+i\eta}(1-t)^{\ell-i\eta} \, dt
$$
