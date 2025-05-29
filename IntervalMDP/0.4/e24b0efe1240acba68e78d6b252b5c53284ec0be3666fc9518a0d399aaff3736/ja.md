```
MixtureIntervalMarkovDecisionProcess{
    P <: IntervalProbabilities,
    VT <: AbstractVector{Int32},
    VI <: Union{AllStates, AbstractVector}
}
```

(定常)混合区間マルコフ決定過程 (OIMDP) を表す型であり、これは各状態の遷移確率が個々のプロセスの遷移確率の積として表現できるIMDPです。

形式的には、$(S, S_0, A, \Gamma, \Gamma_\alpha)$ を区間マルコフ決定過程とし、ここで

  * $$
    S = S_1 \times \cdots \times S_n
    $$

    は、$S_i$ が `i` 番目の周辺の状態の集合である共同状態の集合です。
  * $$
    S_0 \subseteq S
    $$

    は初期状態の集合です。
  * $$
    A
    $$

    はアクションの集合です。
  * $$
    \Gamma = \{\Gamma_{s,a}\}_{s \in S, a \in A}
    $$

    は、各ソース-アクションペアに対する遷移確率の区間曖昧集合の集合であり、$\Gamma_{s,a} = \bigotimes_{i=1}^n \Gamma_{s,a}^i$ で、$\Gamma_{s,a}^i$ は $i$ 番目の周辺に対する区間曖昧集合です。
  * $$
    \Gamma^\alpha = \{\Gamma^\alpha_{s,a}\}_{s \in S, a \in A}
    $$

    は混合のための区間曖昧集合です。

次に、`MixtureIntervalMarkovDecisionProcess` 型は次のように定義されます：インデックス `1:num_states` は $S$ の状態であり、`transition_prob` は $\Gamma$ と $\Gamma^\alpha$ を表します。アクションは `stateptr` によって暗黙的に定義されます（例えば、`transition_prob` の `source_dims` が `(2, 3, 2)` で、`stateptr[3] == 4` および `stateptr[4] == 7` の場合、状態 `CartesianIndex(1, 2, 1)` に対して利用可能なアクションは `[1, 2, 3]` です）、`initial_states` は初期状態の集合 $S_0$ です。初期状態が指定されていない場合、初期状態は `AllStates` で表される $S$ のすべての状態と見なされます。遷移確率の曖昧集合の構造に関する詳細は [MixtureIntervalProbabilities](@ref) および [Theory](@ref) を参照してください。

### フィールド

  * `transition_prob::P`: 遷移確率に関する曖昧集合（構造については [MixtureIntervalProbabilities](@ref) を参照）。
  * `stateptr::VT`: `transition_prob` における各ソース状態の開始位置へのポインタ（すなわち、`transition_prob[k][l][:, stateptr[j]:stateptr[j + 1] - 1]` は、各モデル `k` および軸 `l` に対するソース状態 `j` の遷移確率行列です）で、CSC形式の疎行列における `colptr` のスタイルです。
  * `initial_states::VI`: 初期状態。
  * `num_states::Int32`: 状態の数。

### 例

以下の例は、1次元の2つの `OrthogonalIntervalProbabilities` の単純な混合であり、同じソース/アクションペアを持っています。最初の状態には2つのアクションがあり、2番目の状態には1つのアクションがあります。重み付けの曖昧集合も、同じ3つのソース-アクションペアに対して指定されています。

```jldoctest
prob1 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.0 0.5 0.1
                0.1 0.3 0.2
            ],
            upper = [
                0.5 0.7 0.6
                0.7 0.4 0.8
            ],
        ),
    ),
    (Int32(2),),
)
prob2 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.1 0.4 0.2
                0.3 0.0 0.1
            ],
            upper = [
                0.4 0.6 0.5
                0.7 0.5 0.7
            ],
        ),
    ),
    (Int32(2),),
)
weighting_probs = IntervalProbabilities(; lower = [
    0.3 0.5 0.4
    0.4 0.3 0.2
], upper = [
    0.8 0.7 0.7
    0.7 0.5 0.4
])
mixture_prob = MixtureIntervalProbabilities((prob1, prob2), weighting_probs)

stateptr = Int32[1, 3, 4]
mdp = MixtureIntervalMarkovDecisionProcess(mixture_prob, stateptr)
```
