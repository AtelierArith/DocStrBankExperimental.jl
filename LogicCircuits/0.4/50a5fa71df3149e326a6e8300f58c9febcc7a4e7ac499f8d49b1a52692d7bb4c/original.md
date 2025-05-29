Pretty print BDD as a normal form (CNF or DNF).

Caution: may exponentially explode.

Alternatively, pretty prints using the given glyphs (default `∧`, `∨` and `¬`).

```@example
ϕ = (1 ∧ ¬2) ∨ (2 ∧ 3)
print_nf(α; out = false)
```

```@example
ϕ = (1 ∧ ¬2) ∨ (2 ∧ 3)
print_nf(α; out = false, which = "dnf", glyphs = ['+', '*', '-'])
```
