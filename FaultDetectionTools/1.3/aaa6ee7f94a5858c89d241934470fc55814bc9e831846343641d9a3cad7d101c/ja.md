```
mdIFeval(sysQ::MDFilter, sysm::MDMModel; minimal = false, atol, atol1 = atol, atol2 = atol, rtol, fast = true) -> sysR::MDFilterIF
```

モデル検出フィルタ `sysQ` が複数合成モデル `sysm` に適用されたときの内部形式 `sysR` を計算します。もし `j` 番目のコンポーネントモデル `sysm.sys[j]` が、分割された伝達関数行列 `Gj(λ) = [ Guj(λ)  Gdj(λ) Gwj(λ) Gvj(λ) ]` を持ち、これはそれぞれ `controls`、`disturbances`、`noise`、および `auxiliary` 入力に対応している場合、そして `Qi(λ) = [ Qyi(λ) Qui(λ) ]` が `i` 番目のフィルタ `sysQ.sys[i]` の分割された伝達関数行列であり、これは出力と制御に対応している場合、結果として得られる内部形式 `sysR.sys[i,j]` における（`i` 番目のフィルタ、`j` 番目のモデル）ペアに対応する伝達関数行列 `Rij(λ)` は次のように与えられます。

```
 Rij(λ) = | Qyi(λ)  Qui(λ) | * | Guj(λ)  Gdj(λ) Gwj(λ) Gvj(λ) |
                               |  I      0      0      0      |
```

`minimal = true` の場合は最小記述子実現が計算され、`minimal = false`（デフォルト）の場合は（おそらく）非最小実現が決定されます。

最小実現の計算は、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解を使用するか、またはSVD分解に基づくランク決定に依存するペンシル操作アルゴリズムに依存します。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算努力は高くなります。

もし `(Arij-λErij,Brij,Crij,Drij)` が `sysR.sys[i,j]` のフルオーダー記述子実現であるなら、キーワード引数 `atol1`、`atol2`、および `rtol` はそれぞれ、行列 `Arij`、`Brij`、`Crij`、`Drij` の非ゼロ要素に対する絶対許容誤差、行列 `Erij` の非ゼロ要素に対する絶対許容誤差、そして `Arij`、`Brij`、`Crij`、`Drij` および `Eirj` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `nij*ϵ` であり、ここで `ϵ` は作業用 *マシンイプシロン* で、`nij` はシステム `sysR.sys[i,j]` のオーダーです。キーワード引数 `atol` は `atol1 = atol` および `atol2 = atol` を同時に設定するために使用できます。 ```
