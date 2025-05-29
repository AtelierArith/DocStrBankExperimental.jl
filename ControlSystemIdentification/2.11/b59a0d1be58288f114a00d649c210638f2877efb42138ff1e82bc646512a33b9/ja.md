```
model, x0 = subspaceid(data::InputOutputFreqData,
    Ts = data.Ts,
    nx = :auto;
    cont = false,
    verbose = false,
    r = nx === :auto ? min(length(data) ÷ 20, 20) : 2nx, # 内部モデル次数
    zeroD = false,
    estimate_x0 = true,
    stable = true, 
    svd = svd!,
    Aestimator = \,
    Bestimator = \,
    weights = nothing
)
```

周波数領域でのサブスペースベースの同定を使用して状態空間モデルを推定します。

結果が悪い場合は、特にデータの量が少ない場合は `r` を変更してみてください。

例については[docs](https://baggepinnen.github.io/ControlSystemIdentification.jl/dev/freq/#Statespace)を参照してください。

# 引数:

  * `data`: 周波数領域同定データオブジェクト。
  * `Ts`: データが収集されたサンプル時間
  * `nx`: 希望するモデル次数、整数または `:auto`。
  * `cont`: 連続時間モデルを返しますか？推定された離散時間モデルを変換するために双線形変換が使用されます。関数 `d2c` を参照してください。
  * `verbose`: 情報を印刷しますか？
  * `r`: 内部モデル次数、`nx` 以上でなければなりません。
  * `zeroD`: `D` 行列をゼロに強制します。
  * `estimate_x0`: 初期条件を考慮するための追加パラメータの推定。データが時間領域データのFFTから来ている場合は必要ですが、正確に周期的な入力と過渡状態の適切な処理を使用して周波数応答分析で収集されたデータの場合は必要ないかもしれません。
  * `stable`: モデルが安定するために（[`schur_stab`](@ref)を使用）。
  * `svd`: 使用する `svd` 関数。
  * `Aestimator`: `A` 行列（および初期 `C` 行列）の推定器。
  * `Bestimator`: B/D および C/D 行列の推定器。
  * `weights`: `data` の周波数の数と同じ長さの周波数重みのオプションベクトル。
