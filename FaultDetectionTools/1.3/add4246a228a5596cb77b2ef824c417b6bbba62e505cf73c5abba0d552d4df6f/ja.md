```
fdIFeval(sysQ::FDFilter, sysf::FDIModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::FDFilterIF
```

故障検出フィルタ `sysQ` の内部形式 `sysR` を合成モデル `sysf` に適用して計算します。 `sysf` が分割された伝達関数行列 `G(λ) = [ Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) ]` を持ち、これはそれぞれ `controls`、`disturbances`、`faults`、`noise`、および `auxiliary` 入力に対応し、`Q(λ) = [ Qy(λ) Qu(λ) ]` が故障検出フィルタ `sysQ` の分割された伝達関数行列であり、これは分割されたフィルタ入力として `measurable outputs` と `control inputs` に対応する場合、結果として得られる内部形式 `sysR` の伝達関数行列 `R(λ)` は次のように与えられます。

```
 R(λ) = | Qy(λ)  Qu(λ) | * | Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) |
                           |  I       0     0     0     0   |
```

`minimal = true` の場合は最小記述子実現が計算され、`minimal = false`（デフォルト）の場合はおそらく非最小の実現が決定されます。

最小実現の計算は、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解を使用するか、SVD分解に基づくランク決定に依存するペンシル操作アルゴリズムに依存します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

もし `(Ar-λEr,Br,Cr,Dr)` が `sysR.sys` のフルオーダー記述子実現である場合、キーワード引数 `atol1`、`atol2`、および `rtol` はそれぞれ、行列 `Ar`、`Br`、`Cr`、`Dr` の非ゼロ要素に対する絶対許容誤差、行列 `Er` の非ゼロ要素に対する絶対許容誤差、そして行列 `Ar`、`Br`、`Cr`、`Dr` および `Er` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `nϵ` であり、ここで `ϵ` は作業用 *マシンイプシロン* で、`n` はシステム `sysR` の次数です。キーワード引数 `atol` は `atol1 = atol` および `atol2 = atol` を同時に設定するために使用できます。
