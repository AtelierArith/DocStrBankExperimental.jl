```
IntervalMarkovDecisionProcess{
    P <: IntervalProbabilities,
    VT <: AbstractVector{Int32},
    VI <: Union{AllStates, AbstractVector}
}
```

不確実性が遷移確率の形で区間として表現される（定常的な）区間マルコフ決定過程（IMDP）を表す型です。

形式的には、$(S, S_0, A, \Gamma)$を区間マルコフ決定過程とし、ここで 

  * $$
    S
    $$

    は状態の集合、
  * $$
    S_0 \subseteq S
    $$

    は初期状態の集合、
  * $$
    A
    $$

    は行動の集合、そして
  * $$
    \Gamma = \{\Gamma_{s,a}\}_{s \in S, a \in A}
    $$

    は、各ソース-アクションペアに対する遷移確率の区間曖昧性集合です。

このとき、`IntervalMarkovDecisionProcess`型は次のように定義されます：インデックス`1:num_states`は$S$の状態であり、`transition_prob`は$\Gamma$を表し、アクションは`stateptr`によって暗黙的に定義されます（例えば、`stateptr[3] == 4`かつ`stateptr[4] == 7`の場合、状態3で利用可能なアクションは`[1, 2, 3]`です）、`initial_states`は初期状態の集合$S_0$です。初期状態が指定されていない場合、初期状態は`AllStates`で表される$S$のすべての状態と見なされます。遷移確率の曖昧性集合の構造に関する詳細は、[IntervalProbabilities](@ref)および[Theory](@ref)を参照してください。

### フィールド

  * `transition_prob::P`: 遷移確率の区間で、列はソース/アクションペアを表し、行はターゲット状態を表します。
  * `stateptr::VT`: `transition_prob`内の各ソース状態の開始位置へのポインタ（すなわち、`transition_prob[:, stateptr[j]:stateptr[j + 1] - 1]`はソース状態`j`の遷移確率行列です）で、CSC形式のスパース行列のcolptrスタイルです。
  * `initial_states::VI`: 初期状態。
  * `num_states::Int32`: 状態の数。

### 例

```jldoctest
transition_probs = IntervalProbabilities(;
    lower = [
        0.0 0.5 0.1 0.2 0.0
        0.1 0.3 0.2 0.3 0.0
        0.2 0.1 0.3 0.4 1.0
    ],
    upper = [
        0.5 0.7 0.6 0.6 0.0
        0.6 0.5 0.5 0.5 0.0
        0.7 0.3 0.4 0.4 1.0
    ],
)

stateptr = [1, 3, 5, 6]
initial_states = [1]

mdp = IntervalMarkovDecisionProcess(transition_probs, stateptr, initial_states)
```

遷移確率が各ソース状態の遷移確率のリストとして与えられる`IntervalMarkovDecisionProcess`のコンストラクタもあります。

```jldoctest
prob1 = IntervalProbabilities(;
    lower = [
        0.0 0.5
        0.1 0.3
        0.2 0.1
    ],
    upper = [
        0.5 0.7
        0.6 0.5
        0.7 0.3
    ],
)

prob2 = IntervalProbabilities(;
    lower = [
        0.1 0.2
        0.2 0.3
        0.3 0.4
    ],
    upper = [
        0.6 0.6
        0.5 0.5
        0.4 0.4
    ],
)

prob3 = IntervalProbabilities(;
    lower = [0.0; 0.0; 1.0],
    upper = [0.0; 0.0; 1.0]
)

transition_probs = [prob1, prob2, prob3]
initial_states = [1]

mdp = IntervalMarkovDecisionProcess(transition_probs, initial_states)
```
