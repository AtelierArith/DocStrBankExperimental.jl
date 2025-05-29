```
guesswork_upper_bound(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    make_solver,
    c::AbstractVector = T.(1:length(p)),
    max_retries = 50,
    max_time = Inf,
    num_constraints = Inf,
    verbose::Bool = false,
    num_steps_per_SA_run::Integer = length(p)^2 * 500,
) where {T<:Number} -> NamedTuple
```

`p` と `ρBs` で指定された c-q 状態に関連する推測作業問題の上限を計算します。カスタムコストベクトル `c` をオプションで渡すことができます。キーワード引数 `verbose` が true に設定されている場合、アルゴリズムの各イテレーションに関する情報が出力されます。

キーワード引数 `make_solver` は必須であり、*ソルバーインスタンスを作成する関数*を渡さなければなりません。たとえば、`SCSSolver()` を渡す代わりに、`() -> SCSSolver()` を渡してください。これは、`guesswork_upper_bound` で使用されるアルゴリズムが、1つだけでなく一連の SDP を解決するために必要です。

アルゴリズムには、キーワード引数によって制御される3つの終了基準があります。次のいずれかが発生したときにアルゴリズムは停止します：

  * `max_retries` 回のシミュレーテッドアニーリングの試行が、違反した制約を見つけられなかった。
  * `num_constraints` 制約が双対 SDP に追加された。
  * アルゴリズムの総実行時間が次のイテレーションで `max_time` を超えると予測される。

デフォルトでは、`max_retries` は 50 に設定されており、`num_constraints` と `max_time` は無限大に設定されています。

最後に、キーワード引数 `num_steps_per_SA_run` は、シミュレーテッドアニーリングアルゴリズムの実行時間を制御します。与えられたシミュレーテッドアニーリングの実行内で違反した制約を見つけるために、`num_steps_per_SA_run` を増やしてください。
