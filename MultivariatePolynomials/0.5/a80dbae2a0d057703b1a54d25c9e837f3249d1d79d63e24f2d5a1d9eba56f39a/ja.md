```
struct Term{CoeffType,M<:AbstractMonomial} <: AbstractTerm{CoeffType}
    coefficient::CoeffType
    monomial::M
end
```

`coefficient` と `monomial` の間の乗算の表現。

!!! note
    `coefficient` は `Number` である必要はありません。例えば、多変数多項式であることもあります。多変数の `gcd` を計算する際、実際には他の変数に対する多変数多項式を係数とする一変数の `gcd` として再定式化されます。そのような項を作成するには、`*` の代わりに [`term`](@ref) を使用してください。例えば、`p` が多項式で `m` が単項式である場合、`p * m` は `p` の各項を `m` と乗算しますが、`term(p, m)` は `p` を係数とし `m` を単項式とする項を作成します。

