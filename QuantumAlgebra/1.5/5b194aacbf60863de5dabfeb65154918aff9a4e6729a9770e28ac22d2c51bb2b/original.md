```
expval_as_corrs(expr::QuExpr)
```

Take an expression `expr=A B C + D E...` and write its expectation value in terms of correlations $⟨A⟩_c, ⟨B⟩_c, ⟨AB⟩_c, ⟨ABC⟩_c, \ldots$. Note that $⟨A⟩_c = ⟨A⟩$.

E.g., `expval_as_corrs(a'(:n)*a(:n))` returns $⟨a^\dagger_n a_n⟩_c + ⟨a^\dagger_n⟩_c ⟨a_n⟩_c$ (which is equal to $⟨a^\dagger_n a_n⟩$), while `expval_as_corrs(a'(:n)*a(:m)*a(:n))` returns $\langle a_{n}^\dagger a_{m} a_{n} \rangle_{c} + \langle a_{n}^\dagger \rangle_{c} \langle a_{m} \rangle_{c} \langle a_{n} \rangle_{c} + \langle a_{n}^\dagger \rangle_{c} \langle a_{m} a_{n} \rangle_{c} + \langle a_{m} \rangle_{c} \langle a_{n}^\dagger a_{n} \rangle_{c} + \langle a_{n} \rangle_{c} \langle a_{n}^\dagger a_{m} \rangle_{c}$.

See also: [`expval`](@ref), [`corr`](@ref)
