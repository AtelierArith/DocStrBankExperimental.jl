```julia
etaFunction(psi, phi, UT, E, z) -> Any

```

与えられた $\varphi_\alpha$ と $\psi$ に対する統計関数の引数

$$
z_\alpha / U_T  ( (\varphi_\alpha - \psi) + E_\alpha / q ).
$$

パラメータ $E_\alpha$ と $z_\alpha$ はベクトルとして与えられます。この関数は、ポアソン方程式の右辺、すなわち電荷密度を計算するために使用される可能性があります。
