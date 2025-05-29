```julia
fmin(
    fn::Function,
    space::Union{TreeParzen.Types.AbstractDelayed, Dict{Symbol}, AbstractVector},
    N::Int64,
    points::Vector{TreeParzen.Trials.Trial};
    threshold,
    linear_forgetting,
    draws,
    random_trials,
    prior_weight,
    logging_interval
) -> Any

```

提出された関数から最も低い値を返すハイパーパラメータのセットを見つけます。

# 引数

  * `fn` : 評価したい関数。関数は単一の `Dict` を受け取り、`Float64` を返す必要があります。関数が `Dict` を受け取らない場合は、`Dict` の内容を関数が必要とするパラメータに変換するラッピング関数を作成する必要があります。同様に、関数を最小化するのではなく最大化したい場合は、ラッピング関数が出力を反転させる必要があります。例については TreeParzen ユーザーガイドを参照してください。
  * `space` : TreeParzen が検索できるハイパーパラメータの空間を記述する `TreeParzen.HP` モジュールのオブジェクトを含む `Dict`。
  * `N` : 実行する試行の数。
  * `points` : 最適化前に評価されるユーザーによって選択された試行のリスト。リストは空であっても構いません。例: `[Dict(:x => 0.0, :y => 0.0), Dict(:x => 1.0, :y => 2.0)]`

## オプションのキーワード引数

  * `threshold::Float64` : `0` と `1` の間の値で、期待される改善基準がモデル化される確率の閾値を制御します。
  * `linear_forgetting::Int` : 確率モデルに使用される歴史的ポイントの数を制御する正の値で、この数を超える古いポイントは線形的に重み付けが減少します。
  * `draws::Int` : 次の最適化候補の推奨を行う際に引き出すサンプルの数を制御する正の値。
  * `random_trials::Int` : TreeParzen 最適化が使用される前にランダムに生成された候補ポイントの試行の数を制御する正の値。
  * `prior_weight::Float64` : `0` と `1` の間の値で、ユーザー指定の確率パラメータの重要性と試行の履歴との比較を制御します。
  * `logging_interval::Int` : 何回の反復後に進捗ステートメントをログに記録するかを指定する整数。デフォルトは -1 で、完了時のみログに記録されます。
