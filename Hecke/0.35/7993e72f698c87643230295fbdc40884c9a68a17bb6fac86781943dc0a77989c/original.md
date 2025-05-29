```
torsion_structure(E::EllipticCurve{QQFieldElem}) -> (A::Vector{ZZRingElem},
                                       B::Vector{EllipticCurvePoint{QQFieldElem}}
```

Compute the structure of the rational torsion group of an elliptic curve $E$. Then `A` is an array with `A = [n]` resp. `A = [n,m]` such that the rational torsion of $E$ is isomorphic to $\mathbf Z/n\mathbf Z$ resp. $\mathbf Z/n\mathbf Z \times \mathbf Z/m\mathbf Z$. And `B` is an array of points with `B = [P]` and $P$ has order $n$ resp. `B = [P, Q]` and $P$ has order $n$, $Q$ has order $m$.
