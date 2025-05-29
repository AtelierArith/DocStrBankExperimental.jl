```
KalmanFilteringSolution{Tx,Txt,TR,TRt,Tll} <: AbstractFilteringSolution
```

# フィールド

  * `x`: 予測 $x(t+1|t)$ （`plotx=true` の場合にプロットされます）
  * `xt`: フィルタリングされた推定値 $x(t|t)$ （`plotxt=true` の場合にプロットされます）
  * `R`: 予測された共分散行列 $R(t+1|t)$ （`plotR=true` の場合にプロットされます）
  * `Rt`: フィルタ共分散 $R(t|t)$ （`plotRt=true` の場合にプロットされます）
  * `ll`: 対数尤度
  * `e`: 予測誤差 $e(t|t-1) = y - ŷ(t|t-1)$ （`plote=true` の場合にプロットされます）

# プロット

解オブジェクトはプロットできます

```
plot(sol, plotx=true, plotxt=true, plotR=true, plotRt=true, plote=true, plotu=true, ploty=true, plotyh=true, plotyht=true, name="")
```

ここで

  * `plotx`: 予測 `x(t|t-1)` をプロット
  * `plotxt`: フィルタリングされた推定値 `x(t|t)` をプロット
  * `plotR`: 予測された共分散 `R(t|t-1)` を±2σのリボンとしてプロット（正確には1.96σ）
  * `plotRt`: フィルタ共分散 `R(t|t)` を±2σのリボンとしてプロット（正確には1.96σ）
  * `plote`: 予測誤差 `e(t|t-1) = y - ŷ(t|t-1)` をプロット
  * `plotu`: 入力をプロット
  * `ploty`: 測定値をプロット
  * `plotyh`: 予測された測定値 `ŷ(t|t-1)` をプロット
  * `plotyht`: フィルタリングされた測定値 `ŷ(t|t)` をプロット
  * `name`: プロットのラベルに前置きされる文字列で、同じプロット内で複数の解をプロットする際に便利です。

凡例のエントリで使用される信号名を変更するには、[`SignalNames`](@ref) のインスタンスを構築し、`names` キーワード引数を使用してフィルタ（またはプロットコマンドに直接）に渡します。
