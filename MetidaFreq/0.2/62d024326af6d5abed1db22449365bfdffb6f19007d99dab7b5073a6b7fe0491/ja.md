```
diffci(x1, n1, x2, n2; level = 0.95, method = :default)
```

比率の差 (x1 / n1 - x2 / n2) の信頼区間。

  * 'method'
  * `:mn` | `:default`- Miettinen & Nurminen;  Miettinen, O. and Nurminen, M. (1985), 二つの率の比較分析。Statist. Med., 4: 213-226. doi:10.1002/sim.4780040211;
  * `:fm` | `:mee` - Mee最大尤度法; Mee RW (1984) 二つの確率の差のための信頼限界,Biometrics40:1175-1176
  * `:wald` - CCなしのWald CI;
  * `:waldcc` - CCありのWald CI;
  * `:nhs`  - Newcombeのハイブリッド（ウィルソン）スコア区間; Newcombe RG (1998), 独立した比率の差のための区間推定: 十一の方法の比較。Statistics in Medicine 17, 873-890;
  * `:nhscc` - NewcombeのハイブリッドスコアCC; Newcombe (1998);
  * `:ac` -  Agresti-Caffo区間; Agresti A, Caffo B., “比率と比率の差のためのシンプルで効果的な信頼区間は、二つの成功と二つの失敗を加えることから得られる”, American Statistician 54: 280–288 (2000);
  * `:ha` - Hauck-Andersen; Hauck, W. W., & Anderson, S. (1986). 二つの二項確率の差のための大標本信頼区間法の比較。The American Statistician, 40(4), 318–322. doi:10.1080/00031305.1986.10475426 ;
  * `:mover` - 分散推定値回復法;
  * `:jeffrey` - Brown, LiのJeffreys。

# 参考文献:

  * Brown, L.D., Cai, T.T., and DasGupta, A. 二項比率の区間推定。Statistical Science, 16(2):101–117, 2001.
  * Farrington, C. P. and Manning, G. (1990), “非ゼロリスク差または非単位相対リスクの帰無仮説を持つ比較二項試験のための検定統計量とサンプルサイズの公式,” Statistics in Medicine, 9, 1447–1454
  * Li HQ, Tang ML, Wong WK. 分散推定値回復法を用いた二つのポアソン率の比のための信頼区間。Computational Statistics 2014; 29(3-4):869-889
  * Brown, L., Cai, T., & DasGupta, A. (2003). 指数族における区間推定。Statistica Sinica, 13(1), 19-49.
