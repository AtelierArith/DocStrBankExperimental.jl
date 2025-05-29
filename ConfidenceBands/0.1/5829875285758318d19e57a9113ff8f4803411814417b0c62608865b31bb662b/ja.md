```
SuptBand <: PlugInConfidenceBand
```

プラグイン sup-t 信頼帯。実装は Montiel Olea と Plagborg-Møller (2019) のアルゴリズム 1 に従い、一般化された誤差率制御を可能にする場合があります。

`SuptBand` のために計算された臨界値は、正規分布からのランダムドローに基づいています。ランダム数は一度だけ引かれ、エクスポートされていないグローバルオブジェクト `_globalrandnpool` に保存されるため、同じ Julia セッション内で複数回実行しても結果は変わりません。しかし、異なるセッション間で得られる結果は同一ではなく、生成されるランダム数が異なるためです。ランダム数の再現性については、Julia マニュアルの [`Random`](https://docs.julialang.org/en/v1/stdlib/Random/) セクションを参照してください。

# 参考文献

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
