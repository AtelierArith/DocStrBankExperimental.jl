```
MXH(R0::Real, n_coeffs::Integer)
```

Miller拡張調和表現の例としてMXHを返します：

```
R(θ) = R0 + 0.3*R0*cos(θ)
Z(θ) = -0.3*R0*sin(θ)
```

`n_coeffs`のすべてのsin/cos係数はゼロに設定されています。
