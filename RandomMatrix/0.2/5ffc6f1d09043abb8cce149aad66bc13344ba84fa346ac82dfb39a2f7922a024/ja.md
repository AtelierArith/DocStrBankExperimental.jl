```julia
wignersurmise(s ; beta)  
```

  * `beta` : デフォルトは `1`、 

    `1` の間隔密度は GOE(2) に対応します 

    $$
    p_1(s)=\frac{\pi s}{2} e^{-\pi s^{2} / 4}
    $$

    `2` の間隔密度は GUE(2) に対応します 

    $$
    p_2(s)=\frac{32 s^{2}}{\pi^{2}} e^{-4 s^{2} / \pi}
    $$
  * 詳細については [Wigner surmise on Wikipedia](https://en.wikipedia.org/wiki/Wigner_surmise) を参照してください

# 例

GOE の Wigner surmise を `2` で評価します

```julia
wignersurmise(2)

0.1357605281502967
```

GUE の Wigner surmise を `2` で評価します

```julia
wignersurmise(2,beta=2)

0.07962814352725955
```
