モデルicaモデルの線形化モデルを返す関数。この関数は4つの行列A、B、C、Dを返します。

```
linearize(omc; lintime = nothing, simflags= nothing, verbose=true)
```

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。

## キーワード引数

  * `lintime` : モデルの線形化を行う時間を指定する値
  * `simflags`: シミュレーションフラグ、[シミュレーションランタイムフラグ](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/simulationflags.html)を参照。

## linearize() APIの使用例

```julia
linearize(omc)
```

結果ファイルを指定：

```julia
linearize(omc, lintime="0.5")
```

シミュレーションランタイムフラグを設定：

```julia
linearize(omc, simflags="-noEmitEvent")
```
