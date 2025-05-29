```
simulate(omc; resultfile=nothing, simflags="", verbose=false)
```

モデルicaモデルをシミュレートします。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション、`OMCSession()`を参照してください。

## キーワード引数

  * `resultFile::Union{String, Nothing}`: シミュレーション結果を書き込む結果ファイル。
  * `simflags::String`:                   シミュレーションフラグ、[シミュレーションランタイムフラグ](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/simulationflags.html)を参照してください。
  * `verbose::Bool`:                      [debug] コマンド呼び出しを`log.txt`および`error.txt`にログします。

## 例

```julia
simulate(omc)
```

結果ファイルを指定します：

```julia
simulate(omc, resultfile="tmpresult.mat")
```

シミュレーションランタイムフラグを設定します：

```julia
simulate(omc, simflags="-noEmitEvent -override=e=0.3,g=9.3")
```
