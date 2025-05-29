```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix})
```

Creates the discrete switched linear system defined by

$$
x_{k+1} = A_{\sigma_k} x_k, \sigma_k = 1, \ldots, m.
$$

where `m` is the length of `A`.

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, S::AbstractVector)
```

Creates the state dependent discrete switched linear system defined by

$$
x_{k+1} = A_{\sigma_k} x_k, \sigma_k = 1, \ldots, m, x_k \in S[\sigma_k].
$$

where `m` is the length of `A` and `S`.

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, G::AbstractAutomaton)
```

Creates the constrained discrete switched linear system defined by

$$
x_{k+1} = A_{\sigma_k} x_k,
$$

where $\sigma_1, \ldots, \sigma_k$ is a valid sequence of events of the automaton `G`.

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, G::AbstractAutomaton, S::AbstractVector)
```

Creates the state-dependent constrained discrete switched linear system defined by

$$
x_{k+1} = A_{\sigma_k} x_k, x_k \in S[q_k]
$$

where $q_0, \sigma_1, q_1, \ldots, q_{k-1}, \sigma_k, q_k$ is a valid sequence of events of the automaton `G` with intermediate states $q_0, \ldots, q_k$.
