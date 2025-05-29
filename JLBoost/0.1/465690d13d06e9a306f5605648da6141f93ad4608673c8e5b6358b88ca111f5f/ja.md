```
gini(score, target; plotauc = false)
```

`gini = (AUC - 0.5)/0.05 = 2AUC - 1` を返します。AUCは曲線の下の面積であり、giniは（AUCから下の三角形の面積を引いたもの）対（上の三角形の面積）の比率です。

AUCにおいて、ランダムモデルのAUCは0.5ですが、giniにおいてランダムモデルのginiは0.0です。

プロットを生成するには、`plotauc=true`を設定します。
