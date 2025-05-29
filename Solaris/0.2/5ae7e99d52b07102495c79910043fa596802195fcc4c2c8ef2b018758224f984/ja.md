```julia
struct FnDense{F, F2} <: Solaris.AbstractExplicitLayer
```

関数密な層

## フィールド

  * `in`: 入力サイズ
  * `out`: 出力サイズ
  * `σ`: 活性化関数
  * `initial_params`: 初期化方法
  * `bias`: バイアス項を含めるかどうか
