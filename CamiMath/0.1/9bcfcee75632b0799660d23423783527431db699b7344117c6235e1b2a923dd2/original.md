```
CGC(j1::Real, m1::Real, j2::Real, m2::Real, J::Real, M::Real [; msg=true])
```

Clebsch-Gordan coefficient (CGC). This is a vector-coupling coefficient in Dirac notation. The CGCs are zero unless $Δ(j_{1},j_{2},j_{3})>0$ (triangle inequality holds) and $M=m_{1}+m_{2}$. The relation to the Wigner 3j symbols is given by:

$$
\langle j_{1}m_{1};j_{2}m_{2}|JM\rangle\equiv
(-1)^{j_{1}-j_{2}+M}\sqrt{2J+1}\left(\begin{array}{ccc}
j_{1} & j_{2} & J\\
m_{1} & m_{2} & -M
\end{array}\right)
$$

#### Example:

```
julia> j1=3; m1=0; j2=4; m2=-1; J=5; M=-1;

julia> o = CGC(j1, m1, j2, m2, J, M); println(" = $o")
-√(361/2730) = -0.36364052611670255269921486774521555203216489725107181148303161368088211274565

julia> o = CGC(j1, m1, j2, m2, J, M; msg=false); println(o)
-0.36364052611670255269921486774521555203216489725107181148303161368088211274565

julia> o = (-1)^(j1-j2+M) * sqrt(2J+1) * threeJsymbol(j1, m1, j2, m2, J, -M; msg=false); println(o)
-0.36364052611670255269921486774521555203216489725107181148303161368088211274565

julia> CGC(3, 0, 4, -1, 5, -1);
-√(361/2730)
```
