```julia
massflow_summary_parallel!(
    systems::Vector{Santiago.System},
    M_in::Dict;
    MC,
    n,
    techflows,
    scale_reliability
)

```

モンテカルロ質量フロー計算を実行し、各システムに要約統計を追加します *マルチスレッドを使用して*。Juliaを複数のスレッドで起動することを確認してください！

## 引数:

  * `M_in`: 各ソースの各物質の流入を含む辞書。
  * `MC`: falseの場合、ディリクレ分布の期待値が移転係数として使用されます。そうでない場合、移転係数はディリクレ分布からサンプリングされます。

## キーワード引数

  * `n`: モンテカルロシミュレーションの数。`MC=false`の場合は無視されます。
  * `techflows`: trueの場合、個々の技術のフローが要約されます。
  * `scale_reliability`: すべての`Techs`の`transC_reliability`をスケールするための係数。
  * `rng`: オプション、乱数生成器。これは、スレッドセーフを取得するためにマルチスレッドにのみ必要です。
