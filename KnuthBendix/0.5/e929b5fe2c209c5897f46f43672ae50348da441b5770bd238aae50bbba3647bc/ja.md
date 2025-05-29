```
WreathOrder{T,S} <: RewritingOrdering
WreathOrder(A::Alphabet; levels[, order=collect(A)])
```

単語は最初にそのレベルで比較され、次に接頭辞に対する再帰で引き分けられます。

`levels` ベクトルは、各文字に **アルファベットに現れる順に** レベルを割り当て、単語の `level` はそのすべての文字のレベルの最大値です。

順序は単語を最初にそのレベルで比較し、次に純粋な最大レベルの単語の `LenLex` 順序で引き分けます。さらに引き分けは、低いレベルの接頭辞に対する再帰によって解決されます。

# 定義

`U = U₀·a₁·U₁·…·aᵣ·Uᵣ` を `U` の分解とし、次の条件を満たすものとします。

  * すべての `aᵢ` は同じ（最大の）レベルにあり、
  * 各 `Uᵢ` は厳密に小さいレベルにあります。

`V = V₀·b₁·V₁·…·bₛ·Vₛ` を同様の分解とします。すると `U <≀ V` であるのは次のいずれかの場合です。

  * `a₁·…·aᵣ < b₁·…·bₛ` が `LenLex` 順序に従う場合、または
  * `a₁·…·aᵣ = b₁·…·bₛ` かつ `U₀ <≀ V₀`、または `Uᵢ = Vᵢ` で `0≤i<k` だが `Uₖ <≀ Vₖ` の場合。

詳細については、次の文献を参照してください。

> 1. C. Sims *Computation with finitely presented groups*, p. 46-47
> 2. D. Holt, B. Eick and E. O’Brien *Handbook of Computational Group Theory*, Section 12.4 Rewriting systems for polycyclic groups, p. 426-427
> 3. S. Rees *Automatic groups associated with word orders other than shortlex* Section 5.3 Wreath product orders.


# 例

```jldoctest
julia> X = Alphabet([:a, :b]);

julia> a, b = Word([1]), Word([2]);

julia> wro = WreathOrder(X, levels = [1, 2])
WreathOrder: a(1) < b(2)

julia> lt(wro, a^100, a * b * a^2) # レベルのみで
true

julia> lt(wro, b^2*a, a^2 * b * a) # 最大レベルの単語で
false

julia> lt(wro, a * b * a^2, a^2 * b * a) # 低いレベルの接頭辞で
true
```
