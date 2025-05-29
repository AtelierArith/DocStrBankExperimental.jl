```
simulate(cp::AbstractControlProblem, args...; kwargs...)
```

制御されたシステムをランダムな軌道のファミリーに対してシミュレートします。

### 入力

  * `cp`           – 制御問題
  * `trajectories` – （オプション、デフォルト: `10`）シミュレートされた軌道の数

### 出力

`EnsembleSimulationSolution` 型のオブジェクト。

### 注意事項

この関数は [`OrdinaryDiffEq.jl`](https://github.com/SciML/OrdinaryDiffEq.jl) のアンサンブルシミュレーション機能を使用します。
