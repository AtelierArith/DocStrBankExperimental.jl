```
GenericCubicEOS(mixture)
GenericCubicEOS(mixture, PengRobinson())
```

`MultiComponentMixture`と指定されたEOSのための一般的な立方体状態方程式をインスタンス化します。

現在サポートされている第二引数の選択肢：

```
1. `PengRobinson()` (デフォルト)
2. `PengRobinsonCorrected()`
3. `ZudkevitchJoffe()`
4. `RedlichKwong()`
5. `SoaveRedlichKwong()`
```
