```
minkowski_sum(P::AbstractPolyhedron, Q::AbstractPolyhedron;
              [backend]=nothing, [algorithm]=nothing, [prune]=true)
```

Compute the Minkowski sum of two polyhedra in constraint representation.

### Input

  * `P`         – polyhedron in constraint representation
  * `Q`         – polyhedron in constraint representation
  * `backend`   – (optional, default: `nothing`) polyhedral computations backend
  * `algorithm` – (optional, default: `nothing`) algorithm to eliminate                variables; available options are `Polyhedra.FourierMotzkin`,                `Polyhedra.BlockElimination`, and `Polyhedra.ProjectGenerators`
  * `prune`     – (optional, default: `true`) if `true`, apply a post-processing                to remove redundant constraints

### Output

A polyhedron in H-representation that corresponds to the Minkowski sum of `P` and `Q`.

### Algorithm

This function implements the concrete Minkowski sum by projection and variable elimination as detailed in [Kvasnica05](@citet). The idea is that if we write $P$ and $Q$ in *simple H-representation*, that is, $P = \{x ∈ ℝ^n : Ax ≤ b \}$ and $Q = \{x ∈ ℝ^n : Cx ≤ d \}$, then their Minkowski sum can be seen as the projection onto the first $n$-dimensional coordinates of the polyhedron:

$$
    \begin{pmatrix} 0 & A \ C & -C \end{pmatrix} \binom{x}{y} ≤ \binom{b}{d}
$$

This is seen by noting that $P ⊕ Q$ corresponds to the set of points $x ∈ ℝ^n$ such that $x = y + z$ with $Ay ≤ b$ and $Cz ≤ d$; hence it follows that $Ay ≤ b$ and $C(x-y) ≤ d$, and the inequality above follows by considering the $2n$-dimensional space $\binom{x}{y}$. The reduction from $2n$ to $n$ variables is performed using an elimination algorithm as described next.

The elimination of variables depends on the polyhedra library `Polyhedra`, which itself uses `CDDLib` for variable elimination. The available algorithms are:

  * `Polyhedra.FourierMotzkin`    – projection by computing the H-representation                                  and applying the Fourier-Motzkin elimination                                  algorithm to it
  * `Polyhedra.BlockElimination`  – projection by computing the H-representation                                  and applying the block elimination algorithm                                  to it
  * `Polyhedra.ProjectGenerators` – projection by computing the V-representation
