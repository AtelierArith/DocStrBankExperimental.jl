```
ImmutablePolynomial{T, X, N}(coeffs)
```

係数 `a₀, a₁, …, aₙ` から不変（静的）多項式を構築します。最低次が最初で、オプションで与えられた変数 `x` に関して、`x` は文字、シンボル、または文字列であることができます。

もし $p = a_n x^n + \ldots + a_2 x^2 + a_1 x + a_0$ であれば、`ImmutablePolynomial((a_0, a_1, ..., a_n))` を通じてこれを構築します（`a_n ≠ 0` と仮定）。また、ベクトルや数値を使用して構築することもできます。

通常の算術演算子は、多項式とスカラーの組み合わせだけでなく、多項式同士でも動作するようにオーバーロードされています。ただし、異なる変数の2つの非定数多項式を含む操作はエラーを引き起こします。他の多項式とは異なり、`setindex!` は `ImmutablePolynomials` に対しては定義されていません。

多項式の次数（`+1`）はコンパイル時定数であるため、いくつかのパフォーマンス向上が可能です。たとえば、不変多項式は、Julia 1.4 から提供される `evalpoly` によるより高速な多項式評価を利用できます。同様のメソッドは加算や乗算にも使用されます。

ただし、次数が型に含まれているため、不変多項式間の昇格は共通の型に昇格することができません。そのため、これらは有理関数での使用が制限されます。

!!! note
    `ImmutablePolynomial` は軸を意識しておらず、`coeffs` を単に係数のリストとして扱い、最初のインデックスは常に定数項に対応します。


# 例

```jldoctest
julia> using Polynomials

julia> ImmutablePolynomial((1, 0, 3, 4))
ImmutablePolynomial(1 + 3*x^2 + 4*x^3)

julia> ImmutablePolynomial((1, 2, 3), :s)
ImmutablePolynomial(1 + 2*s + 3*s^2)

julia> one(ImmutablePolynomial)
ImmutablePolynomial(1.0)
```

!!! note
    これは `@tkoolen` による [StaticUnivariatePolynomials](https://github.com/tkoolen/StaticUnivariatePolynomials.jl) をモデルにしています。

