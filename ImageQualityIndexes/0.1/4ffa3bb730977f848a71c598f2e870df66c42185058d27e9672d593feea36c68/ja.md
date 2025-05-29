```
HASLER_AND_SUSSTRUNK_M3 <: NoReferenceIQI
M =  hasler_and_susstrunk_m3(img)
```

自然画像の色彩豊かさを[1]のM3メソッドを使用して計算します。結果の解釈のためのガイドとして、著者は以下を提案しています：

| 属性       |  M3 |
|:-------- | ---:|
| 色彩がない    |   0 |
| やや色彩豊か   |  15 |
| 中程度の色彩豊か |  33 |
| 平均的な色彩豊か |  45 |
| かなり色彩豊か  |  59 |
| 非常に色彩豊か  |  82 |
| 極めて色彩豊か  | 109 |

[1] Hasler, D. and Süsstrunk, S.E., 2003, June. Measuring colorfulness in natural images. In Human vision and electronic imaging VIII (Vol. 5007, pp. 87-96). International Society for Optics and Photonics.
