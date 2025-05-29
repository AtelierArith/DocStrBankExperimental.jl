```julia
struct Satisfiability{S, T, WT<:(AbstractArray{T}), OBJ} <: ProblemReductions.AbstractSatisfiabilityProblem{S, T, OBJ}
```

```
Satisfiability(cnf::CNF{S}, weights::AbstractVector=UnitWeight(length(cnf.clauses)); use_constraints::Bool=false) where {S}
```

Satisfiability (also called SAT) problem is to find the boolean assignment that satisfies a Conjunctive Normal Form (CNF). A tipical CNF would look like:

$$
\left(l_{11} \vee \ldots \vee l_{1 n_1}\right) \wedge \ldots \wedge\left(l_{m 1} \vee \ldots \vee l_{m n_m}\right)
$$

where literals are joint by $\vee$ to for $m$ clauses and clauses are joint by $\wedge$ to form a CNF. The satisfiability problem is to find the assignment that maximizes the number of satisfied clauses if `use_constraints` is `false`, otherwise, the goal is to find one assignment that can satisfy the CNF.

We should note that all the SAT problem problem can be reduced to the 3-SAT problem and it can be proved that 3-SAT is NP-complete.

## Fields

  * `cnf` is a conjunctive normal form ([`CNF`](@ref)) for specifying the satisfiability problems.
  * `weights` are associated with clauses. The solution size is the weighted sum of the number of satisfied assignments.

## Example

In the following example, we define a satisfiability problem with two clauses.

```jldoctest
julia> using ProblemReductions

julia> bv1, bv2, bv3 = BoolVar.(["x", "y", "z"])
3-element Vector{BoolVar{String}}:
 x
 y
 z

julia> clause1 = CNFClause([bv1, bv2, bv3])
x ∨ y ∨ z

julia> clause2 = CNFClause([BoolVar("w"), bv1, BoolVar("x", true)])
w ∨ x ∨ ¬x

julia> cnf_test = CNF([clause1, clause2])
(x ∨ y ∨ z) ∧ (w ∨ x ∨ ¬x)

julia> sat_test = Satisfiability(cnf_test)
Satisfiability{String, Int64, UnitWeight, ProblemReductions.EXTREMA}(["x", "y", "z", "w"], [1, 1], (x ∨ y ∨ z) ∧ (w ∨ x ∨ ¬x))
```
