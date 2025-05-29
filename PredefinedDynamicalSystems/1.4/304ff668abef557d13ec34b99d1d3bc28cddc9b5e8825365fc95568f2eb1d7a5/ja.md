# PredefinedDynamicalSystems.jl

[![](https://img.shields.io/badge/docs-online-blue.svg)](https://JuliaDynamics.github.io/PredefinedDynamicalSystems.jl/dev) [![CI](https://github.com/JuliaDynamics/PredefinedDynamicalSystems.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/PredefinedDynamicalSystems.jl/actions?query=workflow%3ACI) [![Package Downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/PredefinedDynamicalSystems)](https://pkgs.genieframework.com?packages=PredefinedDynamicalSystems)

[DynamicSystems.jl](https://juliadynamics.github.io/DynamicalSystems.jl/dev/)ライブラリで使用できる事前定義された動的システムを含むモジュールです。これをインストールするには、`import Pkg; Pkg.add("PredefinedDynamicalSystems")`を実行します。

事前定義されたシステムは、`DynamicalSystem`インスタンスを返す関数として存在します。アクセス方法は次の通りです：

```julia
ds = PredefinedDynamicalSystems.lorenz(u0; ρ = 32.0)
```

エイリアス`Systems`も非推奨としてエクスポートされています。

**このモジュールは純粋に便利さのために提供されています。実際のテストはなく、将来のバージョンでの安定性は保証されていません。このモジュールは、即席のデモンストレーション例以外の目的で使用することは推奨されません。**

一部のシステムには、ヤコビ行列関数も定義されています。ヤコビ行列関数の命名規則は`\$(name)_jacob`です。したがって、上記の例では`J = Systems.lorenz_jacob`があります。

利用可能なすべてのシステムはドキュメントに提供されており、[オンライン](https://juliadynamics.github.io/PredefinedDynamicalSystems.jl/dev/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドできます。
