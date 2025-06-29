サブC-集合の含意。

(Reyes et al 2004, Proposition 9.1.5) によれば、2つのサブ-$C$-集合 $A,B ↪ X$ に対する含意 $A ⟹ B$ は次のように与えられます。

$$
x ∈ (A ⟹ B)(c) \text{ ならば } ∀f: c → c′, x⋅f ∈ A(c′) ⟹ x⋅f ∈ B(c′)
$$

すべての $c ∈ C$ および $x ∈ X(c)$ に対して。含意の定義と古典論理におけるド・モルガンの法則により、これは次のように同値です。

$$
x ∉ (A ⟹ B)(c) \text{ ならば } ∃f: c → c′, x⋅f ∈ A(c′) ∧ x⋅f ∉ B(c′)
$$

。

この形では、サブC-集合の減算に対する公式とアルゴリズムの二重性を明確に見ることができます ([`subtract`](@ref))。
