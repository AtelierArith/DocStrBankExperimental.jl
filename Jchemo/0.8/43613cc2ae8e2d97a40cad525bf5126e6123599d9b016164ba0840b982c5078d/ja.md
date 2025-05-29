```
pcanipals(; kwargs...)
pcanipals(X; kwargs...)
pcanipals(X, weights::Weight; kwargs...)
pcanipals!(X::Matrix, weights::Weight; kwargs...)
```

NIPALSアルゴリズムによるPCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。タイプ`Weight`でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `gs` : ブール値。`true`の場合（デフォルト）、スコアとローディングのグラム・シュミット直交化が各Xデフレーションの前に行われます。
  * `tol` : 反復を停止するための許容値。
  * `maxit` : 最大反復回数。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正の標準偏差でスケーリングされます。

Dを重みの対角行列（`weights.w`）とし、XをDのメトリックで中心化された行列とします。この関数は、NIPALSによってメトリックDで||X - T * V'||^2を最小化します。

例については関数`pcasvd`を参照してください。

## 参考文献

Andrecut, M., 2009. パラレルGPUによる反復PCAアルゴリズムの実装。計算生物学ジャーナル 16, 1593-1599.  https://doi.org/10.1089/cmb.2008.0221

K.R. Gabriel, S. Zamir, 任意の重みの選択による最小二乗法による行列の低ランク近似、Technometrics 21 (1979) 489–498。

Gabriel, R. K., 2002. バイプロット - 多次元データの探索ツール。フランス統計学会誌、143, 5-55。

Lingen, F.J., 2000. パラレルコンピュータ上での効率的なグラム・シュミット直交化。数値計算における工学の通信 16, 57-66.  https://doi.org/10.1002/(SICI)1099-0887(200001)16:1<57::AID-CNM320>3.0.CO;2-I

Tenenhaus, M., 1998. PLS回帰: 理論と実践。エディション・テクニップ、パリ、フランス。

Wright, K., 2018. パッケージnipals: グラム・シュミット直交化を用いたNIPALSによる主成分分析。  https://cran.r-project.org/
