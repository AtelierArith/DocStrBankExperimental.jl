```
ModelicaSystem(omc, fileName, modelName, library=nothing;
               commandLineOptions=nothing, variableFilter=nothing, customBuildDirectory=nothing)
```

コマンドラインオプションをOMCSessionに設定し、モデル`modelName`をビルドしてシミュレーションの準備をします。

## 引数

  * `omc`:       OpenModelicaコンパイラセッション、`OMCSession()`を参照してください。
  * `fileName`:  Modelicaファイルへのパス。
  * `modelName`: ビルドするModelicaモデルの名前。モデルがModelicaパッケージ内にラップされている場合は、名前空間を含めます。
  * `library`:   依存ライブラリまたはModelicaファイルのリスト。この引数は文字列（例: `"Modelica"`）、タプル（例: `("Modelica", "4.0")`）、配列（例: `["Modelica", "SystemDynamics"]` または `[("Modelica", "4.0"), "SystemDynamics"]`）として渡すことができます。

## キーワード引数

  * `commandLineOptions`: OpenModelicaコマンドラインオプション、[OpenModelica Compiler Flags](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/omchelptext.html)を参照してください。
  * `variableFilter`:     結果ファイル内の変数をフィルタリングするための正規表現。

## 使用法

```
using OMJulia
mod = OMJulia.OMCSession()
ModelicaSystem(mod, "BouncingBall.mo", "BouncingBall", ["Modelica", "SystemDynamics"], commandLineOptions="-d=newInst")
```

依存ライブラリを提供する:

```
using OMJulia
mod = OMJulia.OMCSession()
ModelicaSystem(mod, "BouncingBall.mo", "BouncingBall", ["Modelica", "SystemDynamics", "dcmotor.mo"])
```

さらに[`OMCSession()`](@ref)を参照してください。
