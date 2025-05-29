```
CombinedNextReaction{KeyType,TimeType}()
```

これは次反応法と修正次反応法を組み合わせたものです。次反応法は、GibsonとBruckによる2000年の論文["Efficient Exact Stochastic Simulation of Chemical Systems with Many Species and Many Channels"](https://doi.org/10.1021/jp993732q)からのものです。修正次反応法は、David F. Andersonによる2007年の論文["A modified Next Reaction Method for simulating chemical systems with time dependent propensities and delays"](https://doi.org/10.1063/1.2799998)からのものです。両方の方法は、乱数の引き出しを再利用します。前者は線形空間での分布の生存を蓄積することによって機能し、後者は対数空間での分布の生存を蓄積することによって機能します。

各有効なクロックは、`Distributions`パッケージからの単変量分布を指定します。各分布は、次反応法（線形空間）または修正次反応法（対数空間）の方法でサンプリングされることによって、より正確になります。このサンプラーは、`UnivariateDistribution`のタイプに応じて使用する空間を選択し、パッケージテスト中に行われたパフォーマンスタイミングに基づいています。`Distributions.jl`パッケージに含まれる分布にはデフォルトが設定されています。分布を追加したい場合は、次のように定義します。

```julia
sampling_space(::MyDistribution) = LogSampling
```

ライブラリ内の選択をオーバーライドしたい場合は、指定された分布のサブタイプを作成し、そのサンプリング空間を指定します。

```julia
struct LinearGamma <: Distributions.Gamma end
sampling_space(::LinearGamma) = LinearSampling
```

分布をテストしたい場合は、`tests/nrmetric.jl`を見て、分布のタイミングがどのように行われているかを確認してください。
