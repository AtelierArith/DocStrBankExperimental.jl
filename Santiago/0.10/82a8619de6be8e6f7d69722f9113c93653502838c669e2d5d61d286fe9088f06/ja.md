```julia
massflow_summary(
    sys::Santiago.System,
    M_in::Dict;
    MC,
    n,
    techflows,
    scale_reliability,
    rng
) -> Dict{String, Any}

```

モンテカルロ質量フロー計算を実行し、主な結果の要約統計を提供します。

## 引数:

  * `M_in`: 各ソースの各物質の流入を含む辞書。
  * `MC`: falseの場合、ディリクレ分布の期待値が移転係数として使用されます。そうでない場合、移転係数はディリクレ分布からサンプリングされます。
  * `n`: モンテカルロシミュレーションの数。`MC=false`の場合は無視されます。
  * `scale_reliability`: すべての`Techs`の`transC_reliability`をスケーリングするための係数。
  * `techflows`: trueの場合、個々の技術のフローが要約されます。
  * `rng`: オプション、乱数生成器。これは、スレッドセーフを取得するためにマルチスレッド処理にのみ必要です。
