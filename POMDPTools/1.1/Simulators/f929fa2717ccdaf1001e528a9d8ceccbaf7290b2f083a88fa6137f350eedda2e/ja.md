```
run_parallel(queue::Vector{Sim})
run_parallel(f::Function, queue::Vector{Sim})
```

キュー内の `Sim` オブジェクトを並列で実行し、結果を `DataFrame` として返します。

デフォルトでは、`DataFrame` には各シミュレーションの報酬とシミュレーションに提供されたメタデータが含まれます。

# 引数

  * `queue`: 実行される `Sim` オブジェクトのリスト
  * `f`: 各シミュレーションの結果を処理する関数

この関数は二つの引数を取る必要があります。(1) 実行された `Sim` と (2) シミュレーションの結果、デフォルトでは `SimHistory` です。これはデータフレームに表示される名前付きタプルを返す必要があります。以下の例を参照してください。

## キーワード引数

  * `show_progress::Bool`: 進行状況メーターを表示するかどうか
  * `progress::ProgressMeter.Progress`: 進行状況メーターの表示方法を決定します

# 例

```julia
run_parallel(queue) do sim, hist
    return (n_steps=n_steps(hist), reward=discounted_reward(hist))
end
```

これはステップ数と報酬を含むデータフレームを返します。
