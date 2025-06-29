linearfitxy(X, Y; σX=0, σY=0, r=0, ci=95)

XとYの不確実性を持つ実験データの1D線形フィッティングを行います：

  * 線形フィット:             `Y = a + b*X`                               [1]
  * 誤差:                     $X ± σX;  Y ± σY$                         [2]
  * 誤差の相関:              $r =  = cov(σX, σY) / (σX * σY)$          [3]

# 引数:

  * `X`と`Y`は長さ≥3の入力データベクトルです
  * オプションの標準偏差誤差 $σX$ と $σY$ はベクトルまたはスカラーです
  * オプションの `r` は $σX$ と $σY$ の誤差間の相関です。`r` はベクトルまたはスカラーにできます
  * `ci` は統計の信頼区間です。デフォルトは95%ですが、0より大きく100未満の任意の整数が使用できます。

$$
σX
$$

と $σY$ の誤差（誤差楕円）は二変量ガウス分布を仮定しています。誤差がない場合、または $σX$ または $σY$ のみが提供されている場合、結果は [LsqFit.jl](https://github.com/JuliaNLSolvers/LsqFit.jl) パッケージからのものと同等です。

York et al. (2004) に基づき、拡張（信頼区間、希釈相関係数）があります。

# 例:

```julia-repl
D = linearfitxy(X, Y)    # XとYに誤差なし、プロットは表示されません

D = linearfitxy(X, Y; σX, σY) # XYの誤差は相関なし (r=0);

D = linearfitxy([91., 104, 107, 107, 106, 100, 92, 92, 105, 108], [9.8, 7.4, 7.9, 8.3, 8.3, 9.0, 9.7, 8.8, 7.6, 6.9]);

D = linearfitxy([0.0, 0.9, 1.8, 2.6, 3.3, 4.4, 5.2, 6.1, 6.5, 7.4], [5.9, 5.4, 4.4, 4.6, 3.5, 3.7, 2.8, 2.8, 2.4, 1.5], sx=1 ./ sqrt.([1000., 1000, 500, 800, 200, 80,  60, 20, 1.8, 1]), sy=1 ./ sqrt.([1., 1.8, 4, 8, 20, 20, 70, 70, 100, 500]));

D = linearfitxy([0.037 0.0080; 0.035 0.0084; 0.032 0.0100; 0.040 0.0085; 0.013 0.0270; 0.038 0.0071; 0.042 0.0043; 0.030 0.0160], sx=0.03, sy=0.1, r=0.7071);
```

結果は、ベクトルの場合（`σX σY r`）はGMTdataset構造の新しい列として追加され、スカラーの場合（`a`, `b`, `σa`, `σb`, `σa95`, `σb95`, `ρ` および `S`）は属性として保存されます：

  * 切片 `a`、傾き `b` およびその不確実性 `σa` と `σb`
  * $$
    σa95
    $$

    と $σb95$: 95%信頼区間は二尾t-スチューデント分布を使用、例: $b ± σb95 = b ± t(0.975,N-2)*σb$
  * フィットの良さ `S`（縮小 $Χ²$ テスト）：$Χ²$ N-2 自由度の量 `S ~ 1`: 誤差と一致するフィット、`S > 1`: フィットが悪い、`S >> 1`: 誤差が過小評価されている、`S < 1`: 過剰フィッティングまたは誤差が過大評価されている
  * データ誤差を考慮したピアソンの相関係数 $ρ$

詳細情報と参考文献については、https://github.com/rafael-guerra-www/LinearFitXYerrors.jl のLinearFitXYerrors.jlパッケージを参照してください。
