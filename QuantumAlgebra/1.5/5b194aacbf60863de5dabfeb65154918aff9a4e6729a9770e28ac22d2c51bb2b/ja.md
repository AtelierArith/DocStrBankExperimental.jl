```
expval_as_corrs(expr::QuExpr)
```

式 `expr=A B C + D E...` を取り、その期待値を相関 $⟨A⟩_c, ⟨B⟩_c, ⟨AB⟩_c, ⟨ABC⟩_c, \ldots$ の形で表現します。$⟨A⟩_c = ⟨A⟩$ であることに注意してください。

例えば、`expval_as_corrs(a'(:n)*a(:n))` は $⟨a^\dagger_n a_n⟩_c + ⟨a^\dagger_n⟩_c ⟨a_n⟩_c$ を返します（これは $⟨a^\dagger_n a_n⟩$ に等しいです）。一方、`expval_as_corrs(a'(:n)*a(:m)*a(:n))` は $\langle a_{n}^\dagger a_{m} a_{n} \rangle_{c} + \langle a_{n}^\dagger \rangle_{c} \langle a_{m} \rangle_{c} \langle a_{n} \rangle_{c} + \langle a_{n}^\dagger \rangle_{c} \langle a_{m} a_{n} \rangle_{c} + \langle a_{m} \rangle_{c} \langle a_{n}^\dagger a_{n} \rangle_{c} + \langle a_{n} \rangle_{c} \langle a_{n}^\dagger a_{m} \rangle_{c}$ を返します。

参照: [`expval`](@ref), [`corr`](@ref)
