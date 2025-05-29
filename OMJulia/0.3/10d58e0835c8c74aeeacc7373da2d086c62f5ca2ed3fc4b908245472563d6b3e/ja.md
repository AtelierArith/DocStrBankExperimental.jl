```
ModelicaSystem(omc; modelName, library=nothing,
               commandLineOptions=nothing, variableFilter=nothing, customBuildDirectory=nothing)
```

コマンドラインオプションをOMCSessionに設定し、モデル`modelname`をビルドしてシミュレーションの準備をします。

## 引数

  * `omc`:       OpenModelicaコンパイラセッション、`OMCSession()`を参照してください。

## キーワード引数

  * `modelName`: ビルドするModelicaモデルの名前。モデルがModelicaパッケージ内にラップされている場合は、名前空間を含めます。
  * `library`:   依存ライブラリまたはModelicaファイルのリスト。この引数は文字列（例: `"Modelica"`）またはタプル（例: `("Modelica", "4.0")`）または配列（例: `["Modelica", "SystemDynamics"]` または `[("Modelica", "4.0"), "SystemDynamics"]`）として渡すことができます。
  * `commandLineOptions`: OpenModelicaコマンドラインオプション、[OpenModelica Compiler Flags](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/omchelptext.html)を参照してください。
  * `variableFilter`:     結果ファイル内の変数をフィルタリングするための正規表現。

## 使用法

```
using OMJulia
mod = OMJulia.OMCSession()
ModelicaSystem(mod, modelName="Modelica.Electrical.Analog.Examples.CauerLowPassAnalog", library="Modelica")
```

さらに[`OMCSession()`](@ref)を参照してください。
