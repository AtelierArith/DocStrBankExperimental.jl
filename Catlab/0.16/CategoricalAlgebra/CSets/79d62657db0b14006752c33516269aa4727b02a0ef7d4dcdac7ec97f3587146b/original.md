Implication of sub-C-sets.

By (Reyes et al 2004, Proposition 9.1.5), the implication $A ⟹ B$ for two sub-$C$-sets $A,B ↪ X$ is given by

$x ∈ (A ⟹ B)(c) iff ∀f: c → c′, x⋅f ∈ A(c′) ⟹ x⋅f ∈ B(c′)$

for all $c ∈ C$ and $x ∈ X(c)$. By the definition of implication and De Morgan's law in classical logic, this is equivalent to

$x ∉ (A ⟹ B)(c) iff ∃f: c → c′, x⋅f ∈ A(c′) ∧ x⋅f ∉ B(c′)$.

In this form, we can clearly see the duality to formula and algorithm for subtraction of sub-C-sets ([`subtract`](@ref)).
