ME-NeuralFMUを構築します。FMUはNN内の任意の位置にあります。

# 引数

```
- `fmu` NN内で考慮されるFMU 
- `model` NNトポロジー（例：Flux.chain）
- `tspan` シミュレーション時間範囲
- `solver` ODEソルバー（デフォルト=`nothing`、ヒューリスティックに決定）
```

# キーワード引数

```
- `recordValues` 内部FMU変数を追加で記録します
```
