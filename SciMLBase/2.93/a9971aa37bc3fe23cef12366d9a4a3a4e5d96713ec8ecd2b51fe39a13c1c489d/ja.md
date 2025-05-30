```julia
struct EnsembleSummary{T, N, Tt, S, S2, S3, S4, S5} <: SciMLBase.AbstractEnsembleSolution{T, N, S}
```

`EnsembleSummary`型は、一般的な要約統計を分析するのに役立つように含まれています。2つのコンストラクタが提供されています：

```julia
EnsembleSummary(sim; quantiles = [0.05, 0.95])
EnsembleSummary(sim, ts; quantiles = [0.05, 0.95])
```

最初のものは、各時間ステップでの`(mean,var)`要約を生成します。要約統計と同様に、これはすべての時間ステップが同じであることを前提としています。2番目のものは、`ts`の各時間点`t`での`(mean,var)`要約を生成します。これは、解を補間する能力を必要とします。分位数は、各時間点での`qlow`および`qhigh`分位数を決定するために使用されます。デフォルトでは、5%および95%の分位数が使用されます。

## プロットレシピ

`EnsembleSummary`には、要約統計を視覚化するためのプロットレシピが付属しています。追加のキーワード引数は次のとおりです：

  * `idxs`: プロットする解のコンポーネント。デフォルトではすべてのコンポーネントをプロットします。
  * `error_style`: エラーをプロットするスタイル。デフォルトは`ribbon`です。他の選択肢は、エラーバーのための`:bars`と、エラーバーなしのための`:none`です。
  * `ci_type` : デフォルトは`:quantile`で、`(qlow,qhigh)`分位数の限界は`EnsembleSummary`を構築する際に決定されました。ガウスCI `1.96*(標準誤差)`は、`ci_type=:SEM`を使用して設定できます。

便利な引数の1つは`fillalpha`で、平均値の周りのリボンの透明度を制御します。
