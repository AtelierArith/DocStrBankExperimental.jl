```
model, nls_model, sol = bpdn_model(args...; kwargs...)
model, nls_model, sol = bpdn_model(compound = 1, args...; kwargs...)
```

同じ基底追求デノイズ問題を表す`NLPModel`のインスタンスと`NLSModel`のインスタンスを返します。すなわち、過小決定線形最小二乗目的

½ ‖Ax - b‖₂²,

ここでAは直交正規行列であり、b = A * x̄ + ϵ、x̄はスパースであり、ϵは平均ゼロおよび標準偏差σの正規分布に従うノイズベクトルです。

## 引数

  * `m :: Int`: Aの行数
  * `n :: Int`: Aの列数（`n` ≥ `m`）
  * `k :: Int`: x̄の非ゼロ要素の数
  * `noise :: Float64`: ノイズの標準偏差σ（デフォルト: 0.01）。

第二の形式は、次の引数で第一の形式を呼び出します。

```
m = 200 * compound
n = 512 * compound
k =  10 * compound
```

## キーワード引数

  * `bounds :: Bool`: モデルに非負制約を含めるかどうか（デフォルト: false）。

## 戻り値

同じ基底追求デノイズ問題を表す`FirstOrderModel`と`FirstOrderNLSModel`のインスタンス、および正確な解x̄を返します。

`bounds == true`の場合、x̄の正の部分が返されます。
