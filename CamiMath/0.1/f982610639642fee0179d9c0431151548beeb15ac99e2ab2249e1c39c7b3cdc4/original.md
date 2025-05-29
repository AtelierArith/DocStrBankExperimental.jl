```
threeJsymbol(j1::Real, m1::Real, j2::Real, m2::Real, j3::Real, m3::Real [; msg=true])
```

Wigner 3j symbol. This is a vector coupling coefficient with optimized symmetry properties. The 3j symbols are zero unless $Δ(j_{1},j_{2},j_{3})>0$ (triangle inequality holds) and $m_{1}+m_{2}+m_{3}=0$. The implementation is based on the Racah formula:

$$
\left(\begin{array}{ccc}
j_{1} & j_{2} & j_{3}\\
m_{1} & m_{2} & m_{3}
\end{array}\right)=
(-1)^{j_{1}-j_{2}-m_{3}}\sqrt{\Delta(j_{1}j_{2}J)}\\\times
\sqrt{\left(j_{1}+m_{1}\right)!
\left(j_{1}-m_{1}\right)!
\left(j_{2}+m_{2}\right)!
\left(j_{2}-m_{2}\right)!
\left(j_{3}+m_{3}\right)!
\left(j_{3}-m_{3}\right)!}
\\\times\sum_{t}\frac{(-)^{t}}{t!(j_{3}-j_{2}+t+m_{1})!
(j_{3}-j_{1}+t-m_{2})!
(j_{1}+j_{2}-j_{3}-t)!(j_{1}-t-m_{1})!(j_{2}-t+m_{2})!}
$$

#### Example:

```
julia> o = threeJsymbol(3, 0, 4, -1, 5, 1); println(" = $o")
-√(361/30030) = -0.1096417439724123565166029917781360897459044055433631161836138910409772907333476

julia> threeJsymbol(3, 0, 4, -1, 5, 1; msg=false)
-0.1096417439724123565166029917781360897459044055433631161836138910409772907333476

julia> threeJsymbol(0, 0, 0, 0, 0, 0; msg=false)
1.0
```
