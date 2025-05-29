```
range(start::T; stop::T, length=100) where T<:Colorant
range(start::T, stop::T; length=100) where T<:Colorant
```

`start`から`stop`までの線形補間されたランプでN (=`length`) >2の色を生成し、色の`Array`を返します。

!!! compat "Julia 1.1"
    `stop`を位置引数として使用するには、少なくともJulia 1.1が必要です。

