```
AbstractDIDResult{TR<:AbstractTreatment} <: StatisticalModel
```

すべてのタイプの差分-in-差分の推定結果を収集するインターフェースのスーパタイプで、`TR`型の治療を含みます。

# インターフェース定義

| 必要なメソッド           | デフォルト定義                                        | 簡単な説明                                                                |
|:----------------- |:---------------------------------------------- |:-------------------------------------------------------------------- |
| `coef(r)`         | `r.coef`                                       | 共変量を含むすべての係数のポイント推定値のベクトル                                            |
| `vcov(r)`         | `r.vcov`                                       | `coef`の推定値に対する分散共分散行列                                                |
| `vce(r)`          | `r.vce`                                        | 共分散推定量                                                               |
| `confint(r)`      | tまたは正規分布に基づく                                   | `coef`の推定値に対する信頼区間                                                   |
| `treatment(r)`    | `r.tr`                                         | 治療の仕様                                                                |
| `nobs(r)`         | `r.nobs`                                       | 推定に関与する観測数（テーブル行）                                                    |
| `outcomename(r)`  | `r.yname`                                      | 結果変数の名前                                                              |
| `coefnames(r)`    | `r.coefnames`                                  | 共変量を含むすべての係数の名前（`Vector{String}`）                                    |
| `treatcells(r)`   | `r.treatcells`                                 | 共変量なしで`coefnames`の順序で治療係数の`Tables.jl`互換の表形式の説明                       |
| `weights(r)`      | `r.weights`                                    | サンプルウェイトを含む列の名前（指定されている場合）                                           |
| `ntreatcoef(r)`   | `size(treatcells(r), 1)`                       | 治療係数の数                                                               |
| `treatcoef(r)`    | `view(coef(r), 1:ntreatcoef(r))`               | 治療係数のビュー                                                             |
| `treatvcov(r)`    | `(N = ntreatcoef(r); view(vcov(r), 1:N, 1:N))` | 治療係数のための分散共分散行列のビュー                                                  |
| `treatnames(r)`   | `coefnames(r)[1:ntreatcoef(r)]`                | 治療係数の名前（`Vector{String}`）                                            |
| **オプションメソッド**     |                                                |                                                                      |
| `parent(r)`       | `r.parent` または `r`                             | `r`が生成される結果オブジェクト                                                    |
| `dof_residual(r)` | `r.dof_residual` または `nothing`                 | 残差自由度                                                                |
| `responsename(r)` | `outcomename(r)`                               | 結果変数の名前                                                              |
| `coefinds(r)`     | `r.coefinds` または `nothing`                     | 名前による推定値の取得のための`coefnames`から整数インデックスへのルックアップテーブル（`Dict{String,Int}`） |
| `ncovariate(r)`   | `length(coef(r)) - ntreatcoef(r)`              | 共変量係数の数                                                              |
