```
AllOverlaps(n_replicas=2; operator=nothing, transform=nothing, vecnorm=true)
    <: ReplicaStrategy{n_replicas}
```

Run `n_replicas` replicas and report overlaps between all pairs of replica vectors. If `operator` is not `nothing`, the overlap `dot(c1, operator, c2)` is reported as well. If `operator` is a tuple of operators, the overlaps are computed for all operators.

Column names in the report are of the form `c{i}_dot_c{j}` for vector-vector overlaps, and `c{i}_Op{k}_c{j}` for operator overlaps.

See [`ProjectorMonteCarloProblem`](@ref), [`ReplicaStrategy`](@ref) and [`AbstractOperator`](@ref Interfaces.AbstractOperator) (for an interface for implementing operators).

# Transformed Hamiltonians

If a transformed Hamiltonian `G` has been passed to [`ProjectorMonteCarloProblem`](@ref) then overlaps can be calculated by passing the same transformed Hamiltonian to `AllOverlaps` by setting `transform=G`. A warning is given if these two Hamiltonians do not match.

Implemented transformations are:

  * [`GutzwillerSampling`](@ref)
  * [`GuidingVectorSampling`](@ref)

In the case of a transformed Hamiltonian the overlaps are defined as follows. For a similarity transformation `G` of the Hamiltonian (see e.g. [`GutzwillerSampling`](@ref).)

$$
    \hat{G} = f \hat{H} f^{-1}.
$$

The expectation value of an operator $\hat{A}$ is

$$
    \langle \hat{A} \rangle = \langle \psi | \hat{A} | \psi \rangle
        = \frac{\langle \phi | f^{-1} \hat{A} f^{-1} | \phi \rangle}{\langle \phi | f^{-2} | \phi \rangle}
$$

where

$$
    | \phi \rangle = f | \psi \rangle
$$

is the (right) eigenvector of $\hat{G}$ and $| \psi \rangle$ is an eigenvector of $\hat{H}$.

For a K-tuple of input operators $(\hat{A}_1, ..., \hat{A}_K)$, overlaps of $\langle \phi | f^{-1} \hat{A} f^{-1} | \phi \rangle$ are reported as `c{i}_Op{k}_c{j}`. The correct vector-vector overlap $\langle \phi | f^{-2} | \phi \rangle$ is reported *last* as `c{i}_Op{K+1}_c{j}`. This is in addition to the *bare* vector-vector overlap $\langle \phi | f^{-2} | \phi \rangle$ that is reported as `c{i}_dot_c{j}`.

In either case the `c{i}_dot_c{j}` overlap can be omitted with the flag `vecnorm=false`.
