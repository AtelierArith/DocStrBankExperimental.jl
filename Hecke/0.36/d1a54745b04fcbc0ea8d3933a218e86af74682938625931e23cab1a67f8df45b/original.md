```
is_locally_represented_by(U::T, V::T, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) where T <: AbstractSpace -> Bool
```

Given two spaces `U` and `V` over the same algebra `E`, and a prime ideal `p` in the maximal order $\mathcal O_K$ of their fixed field `K`, return whether `U` is represented by `V` locally at `p`, i.e. whether $U_p$ embeds in $V_p$.
