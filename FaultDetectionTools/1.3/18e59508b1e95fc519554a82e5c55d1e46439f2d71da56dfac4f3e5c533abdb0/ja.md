```
 S = mdspec(sysR::MDFilterIF; cdinp = false, atol, atol1 = atol, atol2 = atol, rtol = 0)
```

モデル検出フィルタのコレクションの弱いバイナリ構造行列 `S` を、モデル検出フィルタ内部形式オブジェクト `sysR::MDFilterIF` を使用して計算します。

フィルタの `M × N` 配列 `sysR` に対して、`S` は次のように決定される `M × N` バイナリ配列です。 `(i,j)` 番目のコンポーネントフィルタ `sysR.sys[i,j]` は、入力-出力形式を持ちます。

```
 rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

ここで、ラプラス変換またはZ変換された残差出力 `rij`、制御入力 `u`、外乱入力 `dj`、ノイズ入力 `wj`、および補助入力 `vj` があり、`Ruij(λ)`, `Rdij(λ)`, `Rwij(λ)` および `Rvij(λ)` はそれぞれ対応する伝達関数行列です。次に、`S[i,j] = 1` は、`cdinp = false`（デフォルト）の場合に `Ruij(λ)` が非ゼロであるか、または `cdinp = true` の場合に `[Ruij(λs) Rdij(λs)]` が非ゼロである場合です。それ以外の場合、`S[i,j] = 0` です。

`(Arij-λErij,Brij,Crij,Drij)` が `sysR.sys[i,j]` の記述子実現である場合、キーワード引数 `atol1`, `atol2`, および `rtol` は、それぞれ行列 `Arij`, `Brij`, `Crij`, `Drij` の非ゼロ要素に対する絶対許容誤差、`Erij` の非ゼロ要素に対する絶対許容誤差、および `Arij`, `Brij`, `Crij`, `Drij` および `Eirj` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `nij*ϵ` であり、ここで `ϵ` は作業用 *マシンイプシロン* で、`nij` は `sysR.sys[i,j]` のシステム行列の次数です。キーワード引数 `atol` は、`atol1 = atol` および `atol2 = atol` を同時に設定するために使用できます。
