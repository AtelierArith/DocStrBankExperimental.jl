```
OrthogonalIntervalMarkovDecisionProcess{
    P <: OrthogonalIntervalProbabilities,
    VT <: AbstractVector{Int32},
    VI <: Union{AllStates, AbstractVector}
}
```

(定常)直交区間マルコフ決定過程 (OIMDP) を表す型であり、これは各状態の遷移確率が個々のプロセスの遷移確率の積として表現できるIMDPです。

形式的には、$(S, S_0, A, \Gamma)$ を直交区間マルコフ決定過程 [1] とし、ここで

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

    は、各ソース-アクションペアに対する遷移確率の区間曖昧集合の集合であり、$\Gamma_{s,a} = \bigotimes_{i=1}^n \Gamma_{s,a}^i$ であり、$\Gamma_{s,a}^i$ は $i$ 番目の周辺における区間曖昧集合です。

次に、`OrthogonalIntervalMarkovDecisionProcess` 型は次のように定義されます：インデックス `1:num_states` は $S$ の状態であり、`transition_prob` は $\Gamma$ を表します。アクションは `stateptr` によって暗黙的に定義されます（例えば、`transition_prob` の `source_dims` が `(2, 3, 2)` で、`stateptr[3] == 4` および `stateptr[4] == 7` の場合、状態 `CartesianIndex(1, 2, 1)` に利用可能なアクションは `[1, 2, 3]` です）、`initial_states` は初期状態の集合 $S_0$ です。初期状態が指定されていない場合、初期状態は `AllStates` で表される $S$ のすべての状態と見なされます。遷移確率の曖昧集合の構造に関する詳細については、[OrthogonalIntervalProbabilities](@ref) および [Theory](@ref) を参照してください。

### フィールド

  * `transition_prob::P`: 遷移確率の区間で、列はソース/アクションペアを表し、行は各周辺に沿ったターゲット状態を表します。
  * `stateptr::VT`: `transition_prob` における各ソース状態の開始位置へのポインタ（すなわち、`transition_prob[l][:, stateptr[j]:stateptr[j + 1] - 1]` は、各軸 `l` に対するソース状態 `j` の遷移確率行列です）で、CSC形式の疎行列における `colptr` のスタイルです。
  * `initial_states::VI`: 初期状態です。
  * `num_states::Int32`: 状態の数です。

### 例

`prob1`、`prob2`、および `prob3` がそれぞれ第一、第二、第三軸のための `IntervalProbabilities` であり、[OrthogonalIntervalProbabilities](@ref) の例として定義されていると仮定します。次のコードは、各軸に3つの状態を持つ `OrthogonalIntervalMarkovDecisionProcess` を構築します。各状態のアクションの数は1つであり、すなわちモデルはマルコフ連鎖です。したがって、`stateptr` は単位範囲 `1:num_states + 1` であり、便利なコンストラクタ `OrthogonalIntervalMarkovChain` を代わりに呼び出すことができます。

```jldoctest
prob = OrthogonalIntervalProbabilities((prob1, prob2, prob3), (Int32(3), Int32(3), Int32(3)))
mc = OrthogonalIntervalMarkovChain(prob)
```

[1] Mathiesen, F. B., Haesaert, S., & Laurenti, L. (2024). Scalable control synthesis for stochastic systems via structural IMDP abstractions. arXiv preprint arXiv:2411.11803.
