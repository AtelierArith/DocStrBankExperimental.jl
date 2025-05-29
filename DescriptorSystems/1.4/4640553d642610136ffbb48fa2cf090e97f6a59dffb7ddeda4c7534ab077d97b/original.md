```
 rtfbilin(type = "c2d"; Ts = T, Tis = Ti, a = val1, b = val2, c = val3, d = val4) -> (g, ginv)
```

Build the rational transfer functions of several commonly used bilinear transformations and their inverses.  The resulting `g` describes the rational transfer function `g(δ)` in the bilinear transformation `λ = g(δ)` and  `ginv` describes its inverse transformation `ginv(λ)` in the bilinear transformation `δ = ginv(λ)`. In accordance with the values of `type` and the keyword argument values `Ts`, `Tis`, `a`, `b`, `c`, and `d`,  the resulting `g` and `ginv` contain first order rational transfer functions of the form `g(δ) = (a*δ+b)/(c*δ+d)`  and `ginv(λ) = (d*λ-b)/(-c*λ+a)`, respectively, which satisfy `g(ginv(λ)) = λ` and `ginv(g(δ)) = δ`. 

Depending on the value of `type`, the following types of transformations can be generated  in conjunction with parameters specified in `Ts`, `Tis`, `a`, `b`, `c`, and `d`:

```
"Cayley" - Cayley transformation: `s = g(z) = (z-1)/(z+1)` and `z = ginv(s) = (s+1)/(-s+1)`; 
           the sampling time `g.Ts` is set to the value `T ≠ 0` (default `T = -1`), while `ginv.Ts = 0`;
           g(z) and ginv(s) are also known as the continuous-to-discrete and discrete-to-continuous transformations, respectively; 

"c2d"    - is alias to "Cayley"

"Tustin" - Tustin transformation (also known as trapezoidal integration): `s = g(z) = (2*z-2)/(T*z+T)` and `z = ginv(s) = (T*s+2)/(-T*s+2)`; 
           the sampling time `g.Ts` is set to the value `T ≠ 0` (default `T = -1`), while `ginv.Ts = 0`;
           a nonzero prewarping frequency `freq` can be specified using the keyword parameter `prewarp_freq = freq`;

"Euler"  - Euler integration (or forward Euler integration): `s = g(z) = s = (z-1)/T` and `z = ginv(s) = T*s+1`; 
           the sampling time `g.Ts` is set to the value `T ≠ 0` (default `T = -1`), while `ginv.Ts = 0`;

"BEuler" - Backward Euler integration (or backward Euler integration): `s = g(z) = (z-1)/(T*z)` and `z = ginv(s) = 1/(-T*s+1)`;
           the sampling time `g.Ts` is set to the value `T ≠ 0` (default `T = -1`), while `ginv.Ts = 0`;

"Moebius" - general (Moebius ) bilinear transformation: `λ = g(δ) = (a*δ+b)/(c*δ+d)` and `δ = ginv(λ) = (d*λ-b)/(-c*λ+a)`;  
            the sampling times `g.Ts` and `ginv.Ts` are  set to the values `T` and `Ti`, respectively;
            the default values of the parameters `a`, `b`, `c`, and `d` are `a = 1`, `b = 0`, `c = 0`, and `d = 1`.
            Some useful particular Moebius transformations correspond to the following choices of parameters: 
            - _translation_: `a = 1`, `b ≠ 0`, `c = 0`, `d = 1` (`λ = δ+b`)
            - _scaling_: `a ≠ 0`, `b = 0`, `c = 0`, `d = 1` (`λ = a*δ`)
            - _rotation_: `|a| = 1`, `b = 0`, `c = 0`, `d = 1` (`λ = a*δ`)
            - _inversion_: `a = 0`, `b = 1`, `c = 1`, `d = 0`  (`λ = 1/δ`)

"lft"     - alias to "Moebius" (linear fractional transformation).
```
