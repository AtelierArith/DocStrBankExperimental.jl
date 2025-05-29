```
PNExpansion{N,T,NMax}
```

This object can be multiplied by a scalar or another `PNExpansion` object, and contains a tuple of coefficients.  The coefficients are stored in the order of the expansion, with the zeroth-order coefficient first.  Multiplication by a scalar just multiplies each of the elements.  Multiplication by another `PNExpansion` object is done by convolving the two tuples of coefficients.

Blanchet (2014) defines the post-Newtonian expansion parameter as follows:

> This parameter represents essentially a slow motion estimate $ϵ ∼ 𝑣/𝑐$, where $𝑣$ denotes a typical internal velocity.  By a slight abuse of notation, following Chandrasekhar et al. [...], we shall henceforth write formally $ϵ ≡ 1/𝑐$, even though $ϵ$ is dimensionless whereas $𝑐$ has the dimension of a velocity. Thus, $1/𝑐 ≪ 1$ in the case of post-Newtonian sources. The small post-Newtonian remainders will be denoted $𝒪(1/𝑐^𝑛)$. Furthermore, [...] we shall refer to a small post-Newtonian term with formal order $𝒪(1/𝑐^𝑛)$ relative to the Newtonian acceleration in the equations of motion, as $\frac{𝑛}{2}\text{PN}$.


Therefore, we consider the coefficients of the `PNExpansion` to be a polynomial in $1/𝑐$. Here, the type parameter `N` corresponds to the number of elements actually present in the tuple of coefficients, and `T` is the type of the coefficients.  The `NMax` parameter is the maximum number of elements, related to the usual PN order by

$$
\text{pn_order} = \frac{\texttt{NMax}-1} {2}.
$$

The `N` parameter is not related to the PN order; it is just used by Julia to know how many elements are currently in the coefficients, but is required to be 1 ≤ N ≤ NMax.
