```
xGaunt(l1::Integer, l2::Integer, l3::Integer, m1::Integer, m2::Integer, m3::Integer)
```

Gaunt coefficient with out $1/\sqrt{\pi}$ factor. (This package can only handle integer arithmetic, it is easy to add the factor mannually.)

$$
\begin{aligned}
\mathrm{Gaunt}(l_1 l_2 l_3 m_1 m_2 m_3) &= \int Y_{l_1 m_1}(\theta, \phi) Y_{l_2 m_2}(\theta, \phi) Y_{l_3 m_3}(\theta, \phi) d\Omega \\
&= \sqrt{\frac{(2l_1 + 1)(2l_2 + 1)(2l_3 + 1)}{4\pi}} \begin{pmatrix} l_1 & l_2 & l_3 \\ m_1 & m_2 & m_3 \end{pmatrix} \begin{pmatrix} l_1 & l_2 & l_3 \\ 0 & 0 & 0 \end{pmatrix}. \\
\end{aligned}
$$
