# TransitionsInTimeseries.jl

[![](https://img.shields.io/badge/docs-dev-lightblue.svg)](https://JuliaDynamics.github.io/TransitionsInTimeseries.jl/dev) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaDynamics.github.io/TransitionsInTimeseries.jl/stable) [![CI](https://github.com/JuliaDynamics/TransitionsInTimeseries.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/TransitionsInTimeseries.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/TransitionsInTimeseries.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/TransitionsInTimeseries.jl) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/TransitionsInTimeseries)](https://pkgs.genieframework.com?packages=TransitionsInTimeseries) [![DOI](https://joss.theoj.org/papers/10.21105/joss.06464/status.svg)](https://doi.org/10.21105/joss.06464)

TransitionsInTimeseries.jlは、再現性があり、パフォーマンスが高く、拡張可能で信頼性のある方法で時系列内の遷移を簡単に分析するための無料でオープンソースのソフトウェアです。類似のターゲットアプリケーションを持つ他の既存のソフトウェアとは対照的に、TransitionsInTimeseries.jlは遷移を見つける方法と有意性をテストする方法のための汎用インターフェースを定義しています。このインターフェース内では、ソフトウェアを三つの直交的な方法で簡単に拡張できます。

1. 新しい指標を使用して分析パイプラインを提供します。これらは自己作成したものでも、他のパッケージからインポートしたものでもかまいません。特に後者は、すぐに遷移を示すことができる数千のメトリックを提供します。
2. 遷移を見つけるための新しい分析パイプラインを追加します。
3. 有意性テストの新しい方法を追加します。

TransitionsInTimeseriesは登録されたJuliaパッケージであり、次のコマンドを実行することでインストールできます。

```
] add TransitionsInTimeseries
```

さらなる情報は、[オンライン](https://juliadynamics.github.io/TransitionsInTimeseries.jl/dev/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることができます。

*このパッケージの別名としては、早期警告信号 / レジリエンス指標 / レジームシフト識別子 / 変化点検出器など、他に呼びたい名前があれば何でも構いません！*
