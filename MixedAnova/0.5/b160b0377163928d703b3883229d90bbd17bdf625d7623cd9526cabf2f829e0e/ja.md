```
AnovaResult{M, T, N}
```

`anova`の返されたオブジェクト。

  * `M`は、複数のモデルが提供される場合は`Tuple`のサブタイプであり、そうでない場合はモデルの型です。
  * `T`は`GoodnessOfFit`のサブタイプであり、`FTest`または`LRT`のいずれかです。
  * `N`はパラメータの長さです。

## フィールド

  * `model`: フルモデルまたはテストされたモデルのタプル。
  * `type`: `anova`のタイプ。
  * `dof`: モデルまたは因子の自由度。
  * `deviance`: テスト統計量を計算するための逸脱。詳細については`deviance`を参照してください。
  * `teststat`: テスト統計量の値。
  * `pval`: テスト統計量のp値。
  * `tests`: 追加の統計を含む`NamedTuple`。
