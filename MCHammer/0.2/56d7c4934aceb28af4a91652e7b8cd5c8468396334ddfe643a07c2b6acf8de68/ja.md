```
GBMA_d(price_0, t, rf, exp_vol; rng="none")
```

GBMA_dは、将来の特定の日における株価を予測するための関数です。この関数は、ブラック-ショールズアプローチを使用して、乗法的幾何ブラウン運動を用いて予測を行います。

```
**price_0**: 時点0における株価
**t**: 予測する日数
**rf**: 無リスク金利（通常は国の25年または30年債）
**exp_vol**: 期待されるボラティリティは年率ボラティリティです
**rng**: 結果をシードして予測を再現可能にするために使用されます。デフォルトではnoneに設定されており、これは完全にランダムであることを意味しますが、結果をシードするためにJuliaのrngのいずれかを使用できます。例: *GBMA_d(price_0, t, rf, exp_vol; rng=MersenneTwister(1))*
```
