```
get_steady_states(
    prob::HomotopyContinuationProblem,
    method::HomotopyContinuationMethod;
    show_progress=true,
    sorting="nearest",
    classify_default=true,
    verbose=false
    )
```

`problem`を`swept_parameters`で指定された範囲にわたって`method`で解決し、`fixed_parameters`を一定に保ちます。`swept_parameters`は、記号変数を配列または範囲にマッピングするペアを受け入れます。`fixed_parameters`は、記号変数を数値にマッピングするペアを受け入れます。

### キーワード引数

  * `show_progress`: 進捗バーを表示するかどうかを示します。
  * `sorting`: 連続解の枝を取得するために`sort_solutions`が使用する方法。現在のオプションは、`"hilbert"`（ヒルベルト曲線に沿った1Dソート）、`"nearest"`（最近傍ソート）、および`"none"`です。
  * `classify_default`: `true`の場合、解はデフォルトの分類方法を使用して分類されます。

### 例

単純な調和振動子 $m \ddot{x} + γ \dot{x} + ω_0^2 x = F \cos(ωt)$ を解いて、$ω$の関数として応答を得る

```julia-repl
# HomotopyContinuationProblemオブジェクトを取得したので、定常状態を見つけましょう
julia> range = (ω => range(0.8, 1.2, 100) ) # 解決するための100のパラメータセット
julia> fixed = ParameterList(m => 1, γ => 0.01, F => 0.5, ω_0 => 1)
julia> get_steady_states(problem, range, fixed)

100のパラメータポイントに対する定常状態の結果

    解の枝:   1
       実数のもの:    1
       安定なもの:  1

    クラス: 安定、物理、ホップ、バイナリラベル

```

2次元スイープを実行することも可能です。

```julia-repl
# スイープされたパラメータは固定よりも優先されます -> 同じ固定を使用
julia> range = (ω => range(0.8,1.2,100), F => range(0.1,1.0,10) )

# スイープされたパラメータは固定よりも優先されます -> 固定のFは無視されます
julia> get_steady_states(problem, range, fixed)

1000のパラメータポイントに対する定常状態の結果

    解の枝:   1
       実数のもの:    1
       安定なもの:  1

    クラス: 安定、物理、ホップ、バイナリラベル
```
