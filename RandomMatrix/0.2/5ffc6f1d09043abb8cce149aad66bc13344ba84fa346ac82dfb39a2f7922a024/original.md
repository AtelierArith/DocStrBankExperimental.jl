```julia
wignersurmise(s ; beta)  
```

  * `beta` : default `1`, 

    `1` for the spacing density corresponds to GOE(2) 

    $p_1(s)=\frac{\pi s}{2} e^{-\pi s^{2} / 4}$

    `2` for the spacing density corresponds to GUE(2) 

    $p_2(s)=\frac{32 s^{2}}{\pi^{2}} e^{-4 s^{2} / \pi}$
  * For more info see [Wigner surmise on Wikipedia](https://en.wikipedia.org/wiki/Wigner_surmise)

# Examples

Evaluate Wigner surmise for GOE at `2`

```julia
wignersurmise(2)

0.1357605281502967
```

Evaluate Wigner surmise for GUE at `2`

```julia
wignersurmise(2,beta=2)

0.07962814352725955
```
