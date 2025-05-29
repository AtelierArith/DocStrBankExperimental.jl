```
is_commutative_semiring(a::T, b::T, c::T) where T
```

Check if elements `a`, `b` and `c` satisfied the commutative semiring requirements.

$$
\begin{align*}
(a \oplus b) \oplus c = a \oplus (b \oplus c) & \hspace{5em}\triangleright\text{commutative monoid $\oplus$ with identity $\mathbb{0}$}\\
a \oplus \mathbb{0} = \mathbb{0} \oplus a = a &\\
a \oplus b = b \oplus a &\\
&\\
(a \odot b) \odot c = a \odot (b \odot c)  &   \hspace{5em}\triangleright \text{commutative monoid $\odot$ with identity $\mathbb{1}$}\\
a \odot  \mathbb{1} =  \mathbb{1} \odot a = a &\\
a \odot b = b \odot a &\\
&\\
a \odot (b\oplus c) = a\odot b \oplus a\odot c  &  \hspace{5em}\triangleright \text{left and right distributive}\\
(a\oplus b) \odot c = a\odot c \oplus b\odot c &\\
&\\
a \odot \mathbb{0} = \mathbb{0} \odot a = \mathbb{0}
\end{align*}
$$
