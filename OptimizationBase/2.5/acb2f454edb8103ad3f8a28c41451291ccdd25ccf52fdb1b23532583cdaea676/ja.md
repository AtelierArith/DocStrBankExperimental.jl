```
AutoModelingToolkit <: AbstractADType
```

最適化関数で未指定の導関数を自動的に生成するための AbstractADType の選択。使用法：

```julia
OptimizationFunction(f, AutoModelingToolkit(); kwargs...)
```

これは、[ModelingToolkit.jl](https://github.com/SciML/ModelingToolkit.jl) パッケージの `modelingtookitize` 機能を使用して、`OptimizationFunction` の導関数やその他のフィールドを生成します。このバックエンドは、目的関数とその導関数、制約およびその導関数のための象徴的な式を作成します。`structural_simplify` を通じて、制約の導関数を計算するために必要な操作の数を減らすことができる簡略化を強制します。これは、OptimizationMOI を介して一部のソルバーインターフェースが必要とする表現グラフを自動的に生成します。例えば、[AmplNLWriter.jl](https://github.com/jump-dev/AmplNLWriter.jl) などです。

  * GPU と互換性があります
  * ヘッセ行列ベースの最適化と互換性があります
  * Hv ベースの最適化と互換性があります
  * 制約と互換性があります

未指定の導関数のみが定義されていることに注意してください。例えば、`OptimizationFunction` に `hess` 関数が供給されると、ヘッセ行列は ModelingToolkit を介して生成されません。

## コンストラクタ

```julia
AutoModelingToolkit(false, false)
```

  * `obj_sparse`: 目的のヘッセ行列がスパースであるかどうかを示します。
  * `cons_sparse`: 制約のヤコビ行列とヘッセ行列がスパースであるかどうかを示します。
