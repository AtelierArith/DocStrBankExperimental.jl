```
熱力学
```

湿った熱力学関数、例えば、空気圧（状態方程式の大気）、相転移の潜熱、飽和蒸気圧、および飽和比湿度。

## AbstractParameterSet's

このモジュールで定義された多くの関数は、ClimaParams.jlに依存しています。ClimaParams.jlは、いくつかの関数（例えば、多くの惑星パラメータ）を定義しています。例えば、モル質量比を計算するには：

```julia
import ClimaParams as CP
import Thermodynamics.Parameters as TP
FT = Float64
param_set = TP.ThermodynamicsParameters(FT)
_molmass_ratio = TP.molmass_ratio(param_set)
```

これらのパラメータはこのモジュール全体で広く使用されているため、`param_set`は多くの熱力学関数の引数となります。

## 飽和調整のための数値的方法

飽和調整関数は、次のように設計されています。

  * `sat_adjust_method` 使用する数値的方法をディスパッチするための型

および数値的方法のインスタンスを返す関数。例えば：

  * `sa_numerical_method_ρpq` は数値的方法のインスタンスを返します。これらの関数の1つは、特定の数値的方法と特定の定式化（この場合は `ρ-p-q_tot`）のために定義されなければなりません。

現在、RootSolvers.jlでサポートされている数値的方法は次のとおりです。

  * `NewtonsMethod` は解析的勾配を用いたニュートン法を使用します
  * `NewtonsMethodAD` は自動微分を用いたニュートン法を使用します
  * `SecantMethod` はセカント法を使用します
  * `RegulaFalsiMethod` はレグラ・ファルシ法を使用します
