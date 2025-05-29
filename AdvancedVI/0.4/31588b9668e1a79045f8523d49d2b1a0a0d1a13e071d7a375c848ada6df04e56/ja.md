```
optimize(problem, objective, q_init, max_iter, objargs...; kwargs...)
```

問題 `problem` を対象とした変分目的 `objective` を最適化し、（確率的）勾配を推定します。

変分近似における学習可能なパラメータは、`Optimisers.destructure` を通じて抽出可能であることが期待されます。これには、変分近似が `Functors.@functor` を通じてファンクタとしてマークされている必要があります。

# 引数

  * `objective::AbstractVariationalObjective`: 変分目的。
  * `q_init`: 初期変分分布。変分パラメータは `Optimisers.destructure` を通じて抽出可能でなければなりません。
  * `max_iter::Int`: 最大反復回数。
  * `objargs...`: `objective` に渡される引数。

# キーワード引数

  * `adtype::ADtypes.AbstractADType`: 自動微分バックエンド。
  * `optimizer::Optimisers.AbstractRule`: 推論に使用される最適化手法。（デフォルト: `Adam`。）
  * `averager::AbstractAverager` : パラメータ平均化戦略。（デフォルト: `NoAveraging()`）
  * `operator::AbstractOperator` : 各最適化ステップ後にパラメータに適用されるオペレーター。（デフォルト: `IdentityOperator()`）
  * `rng::AbstractRNG`: 擬似乱数生成器。（デフォルト: `Random.default_rng()`。）
  * `show_progress::Bool`: 進捗バーを表示するかどうか。（デフォルト: `true`。）
  * `callback`: 各反復後に呼び出されるコールバック関数。詳細は以下を参照。（デフォルト: `nothing`。）
  * `prog`: 進捗バーの設定。（デフォルト: `ProgressMeter.Progress(n_max_iter; desc="Optimizing", barlen=31, showspeed=true, enabled=prog)`。）
  * `state::NamedTuple`: 最適化の内部状態の初期値。前回の実行の状態からウォームスタートするために使用されます。（以下の返される値を参照。）

# 戻り値

  * `averaged_params`: アルゴリズムによって生成された変分パラメータで、`averager` に従って平均化されています。
  * `params`: アルゴリズムによって生成された最後の変分パラメータ。
  * `stats`: 最適化中に収集された統計。
  * `state`: 最適化の最終内部状態のコレクション。これは、対応する実行の最後の反復からウォームスタートするために後で使用できます。

# コールバック

コールバック関数 `callback` のシグネチャは次のとおりです。

```
callback(; stat, state, params, averaged_params, restructure, gradient)
```

引数は次のとおりです。

  * `stat`: 現在の反復中に収集された統計。内容は `objective` によって異なります。
  * `state`: 最適化に使用される内部状態のコレクション。
  * `params`: 変分パラメータ。
  * `averaged_params`: 平均化戦略に従って平均化された変分パラメータ。
  * `restructure`: 変分パラメータから変分近似を再構築する関数。`restructure(param)` を呼び出すと、変分近似が再構築されます。
  * `gradient`: 推定された（おそらく確率的な）勾配。

`callback` は、`cb` 内で計算された追加情報を含む `NamedTuple` を返すことができます。これは、現在の対応する反復の統計に追加されます。そうでない場合は、単に `nothing` を返します。
