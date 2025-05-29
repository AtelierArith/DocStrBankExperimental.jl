```
    run_gillespie!(time,n₀,par,execute!,rates!,initrates,population_history[,hstart=0,statistic!])
```

正確な確率的シミュレーションを実行し、`population_history`を返して埋めます。

# 引数

  * `time::AbstracVector`: シミュレーションの時間間隔
  * `n₀`: 初期人口状態
  * `par`: 追加のパラメータ（`execute!`および`rates!`に渡されます）
  * `execute!`: 実行関数
  * `rates!`: レート関数
  * `initrates`: 初期レート
  * `population_history`: 空の人口履歴
  * `hstart=0`: パラメータ変更のための時間シフト *(オプション)*
  * `statistic!`: 追加の統計関数 *(オプション)*

# 拡張ヘルプ

  * `n₀,initrates,population_history`の3つはすべてシミュレーション中に変更されることに注意してください。
  * アルゴリズムは、`execute!`関数が次のシグネチャを持つことを期待しています   `julia   execute!(i::Number,n₀,par)`   ここで、`i`は実行されるイベントであり、人口状態`n₀`はそれに応じて変更されます。   唯一の例外は、`initrates`が辞書として与えられる場合です。その場合、シグネチャは`execute!(i,trait,n₀,initrates,par)`となり、`trait`は変更されるキーです。
  * アルゴリズムは、`rates!`関数が次のシグネチャを持つことを期待しています   `julia   rates!(initrates,n₀,par)`   ここで、レートは現在の人口状態`n₀`に応じて変更されます。
  * アルゴリズムは、`statistic!`関数が次のシグネチャを持つことを期待しています   `julia   statistic!(population_hist,t,n₀,par)`   ここで、人口履歴は位置`t`で現在の人口状態`n₀`に応じて変更されます。
  * `population_history`は、1から`length(time)`までのインデックスでアクセス可能である必要があります。あるいは、`hstart`が与えられた場合は、`1+hstart`から`length(time)+hstart`までです。指定された`statistic!`関数が与えられない限り。
  * 初期人口状態`n₀`は、`population_history`が`population_history :: Vector{typeof(n₀)}`の意味で一致する必要があります。指定された`statistic!`関数が与えられない限り。
  * パラメータ変数`par`はすべての関数（`execute!,rates!,statistics!`）を通じて渡され、ユーザーに追加の柔軟性を提供します。
