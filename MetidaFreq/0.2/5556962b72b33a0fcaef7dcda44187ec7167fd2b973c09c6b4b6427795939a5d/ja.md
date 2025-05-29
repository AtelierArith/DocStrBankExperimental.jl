```
orci(x1, n1, x2, n2; level = 0.95, method = :default)
```

オッズ比信頼区間。

  * `:mn` - MNスコア (Miettinen&Nurminen, 1985);
  * `:fm` | `:mee` - FM (MNスコアと同じだが、`(n1 + n2) * (n1 + n2 - 1)`で掛け算されない) (Mee RW, 1984; Farrington&Manning, 1990);
  * `:woolf` - ウールフロジット (Woolf, 1955);
  * `:awoolf` - 調整ウールフ区間 (Gart調整ロジット) (Gart, 1966; Lawson, 2005);
  * `:mover` - 分散推定回復法 (MOVER) (Donner&Zou, 2012);

参考文献:

  * Miettinen O. S., Nurminen M. (1985) 二つの率の比較分析。Statistics in Medicine 4,213–226;
  * Mee RW (1984) 二つの確率の差に対する信頼限界、Biometrics 40:1175-1176;
  * Farrington, C. P. and Manning, G. (1990), “非ゼロリスク差または非単位相対リスクの帰無仮説を持つ比較二項試験のための検定統計量とサンプルサイズの公式,” Statistics in Medicine, 9, 1447–1454;
  * Woolf, B. (1955). 血液型と病気の関係を推定することについて。Annals of human genetics, 19(4):251-253;
  * Gart, J. J. (1966). コンティンジェンシーテーブルの代替分析。Journal of the Royal Statistical Society. Series B (Methodological), 28:164-179;
  * Lawson, R (2005). オッズ比のための小サンプル信頼区間。Communication in Statistics Simulation and Computation, 33, 1095-1113;
  * Donner, A. and Zou, G. (2012). 正規平均と標準偏差の関数のための閉形式信頼区間。Statistical Methods in Medical Research, 21(4):347-359.
