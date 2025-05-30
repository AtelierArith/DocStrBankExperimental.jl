```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix})
```

離散スイッチ線形システムを定義します。

$$
x_{k+1} = A_{\sigma_k} x_k, \sigma_k = 1, \ldots, m.
$$

ここで、`m` は `A` の長さです。

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, S::AbstractVector)
```

状態依存の離散スイッチ線形システムを定義します。

$$
x_{k+1} = A_{\sigma_k} x_k, \sigma_k = 1, \ldots, m, x_k \in S[\sigma_k].
$$

ここで、`m` は `A` と `S` の長さです。

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, G::AbstractAutomaton)
```

制約付き離散スイッチ線形システムを定義します。

$$
x_{k+1} = A_{\sigma_k} x_k,
$$

ここで、$\sigma_1, \ldots, \sigma_k$ はオートマトン `G` の有効なイベントのシーケンスです。

```
discreteswitchedsystem(A::AbstractVector{<:AbstractMatrix}, G::AbstractAutomaton, S::AbstractVector)
```

状態依存の制約付き離散スイッチ線形システムを定義します。

$$
x_{k+1} = A_{\sigma_k} x_k, x_k \in S[q_k]
$$

ここで、$q_0, \sigma_1, q_1, \ldots, q_{k-1}, \sigma_k, q_k$ はオートマトン `G` の有効なイベントのシーケンスであり、中間状態は $q_0, \ldots, q_k$ です。
