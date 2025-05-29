```
MLESettings(y, model, init, optimizer, ci)
```

推定設定を指定するためのラッパー関数。

  * `y`: 時系列
  * `model`: モデル仕様
  * `init`: 初期値（ベクトルまたはパラメータ）。
  * `optimizer`: 最適化ルーチン。"BFGS"、"LBFGS"または"NelderMead"
  * `ci`: 指標：信頼区間を計算するべきか？
  * `maxEval`: 最大尤度評価回数

# 例

```julia-repl
MLESettings(y, model, ci = true, maxEval = 1e9)
```

引数 `init` が指定されていない場合、有効な初期値が選択されます。詳細は [MLEControl](@ref) を参照してください。
