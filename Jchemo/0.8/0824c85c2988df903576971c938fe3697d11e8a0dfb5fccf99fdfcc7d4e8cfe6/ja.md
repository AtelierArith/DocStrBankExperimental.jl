```
sampdp(X, k::Int; metric = :eucl)
```

DUPLEXサンプリングによるトレーニングセットとテストセットの構築。

  * `X` : Xデータ (n, p)。
  * `k` : サンプリングする観測値のペア数 (トレーニング/テスト)。n / 2以下でなければなりません。

キーワード引数:

  * `metric` : 距離計算に使用されるメトリック。可能な値は: `:eucl` (ユークリッド)、`：mah` (マハラノビス)。

3つの出力（データの行インデックス）が返されます:

  * `train` (`k`),
  * `test` (`k`),
  * `remain` (n - 2 * `k`)。

出力 `train` と `test` はDUPLEXアルゴリズム (Snee, 1977 p.421) に基づいて構築されます。これらは、ほぼ同じX空間領域をカバーし、類似の統計的特性を持つことが期待されます。

実際には、出力 `remain` が空でない場合（つまり、残りの観測値がある場合）、一般的な戦略はそれを出力 `train` に追加することです。

## 参考文献

Kennard, R.W., Stone, L.A., 1969. Computer aided design of experiments. Technometrics, 11(1), 137-148.

Snee, R.D., 1977. Validation of Regression Models: Methods and Examples. Technometrics 19, 415-428. https://doi.org/10.1080/00401706.1977.10489581

## 例

```julia
using Jchemo

X = [0.381392  0.00175002 ; 0.1126    0.11263 ; 
    0.613296  0.152485 ; 0.726536  0.762032 ;
    0.367451  0.297398 ; 0.511332  0.320198 ; 
    0.018514  0.350678] 

k = 3
sampdp(X, k)
```
