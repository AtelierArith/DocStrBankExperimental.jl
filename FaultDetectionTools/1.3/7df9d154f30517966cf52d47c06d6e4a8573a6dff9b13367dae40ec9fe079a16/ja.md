```
fdIFeval(sysQ::FDIFilter, sysf::FDIModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::FDIFilterIF
```

故障検出および隔離フィルタ `sysQ` の内部形式 `sysR` を合成モデル `sysf` に適用して計算します。 `sysf` が分割された伝達関数行列 `G(λ) = [ Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) ]` を持ち、これはそれぞれ `controls`、`disturbances`、`faults`、`noise` および `auxiliary` 入力に対応しています。また、`Qi(λ) = [ Qyi(λ) Qui(λ) ]` は、分割されたフィルタ入力として `measurable outputs` と `control inputs` に従った `i` 番目のフィルタ `sysQ.sys[i]` の分割された伝達関数行列である場合、結果の内部形式 `sysR.sys[i]` における `i` 番目のフィルタの伝達関数行列 `Ri(λ)` は次のように与えられます。

```
 Ri(λ) = | Qyi(λ)  Qui(λ) | * | Gu(λ)  Gd(λ) Gf(λ) Gw(λ) Gv(λ) |
                              |  I       0     0     0     0   |
```

`minimal = true` の場合、最小記述子実現が計算され、`minimal = false`（デフォルト）の場合はおそらく非最小実現が決定されます。

最小実現の計算は、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解を使用するか、またはSVD分解に基づくランク決定に依存するペンシル操作アルゴリズムに依存しています。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

もし `(Ari-λEri,Bri,Cri,Dri)` が `sysR.sys[i]` のフルオーダー記述子実現である場合、キーワード引数 `atol1`、`atol2`、および `rtol` はそれぞれ、行列 `Ari`、`Bri`、`Cri`、`Dri` の非ゼロ要素に対する絶対許容誤差、行列 `Eri` の非ゼロ要素に対する絶対許容誤差、そして `Ari`、`Bri`、`Cri`、`Dri` および `Eir` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `ni*ϵ` であり、ここで `ϵ` は作業用 *マシンイプシロン* で、`ni` はシステム `sysR.sys[i]` の次数です。キーワード引数 `atol` は、同時に `atol1 = atol` および `atol2 = atol` を設定するために使用できます。
