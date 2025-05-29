```
MultiBandPhotosyntheticallyActiveRadiation{F, FN, K, E, C, SPAR, SPARD}
```

複数の波長帯を持つ光減衰モデルで、各帯 (i) は次のように減衰します：

```
∂PARᵢ(z)/∂z = PARᵢ(kʷ(i) + χ(i)Chl(z)ᵉ⁽ⁱ⁾)
```

ここで、kʷ(i) は帯特有の水減衰係数、e(i) はクロロフィル指数、χ(i) はクロロフィル減衰係数です。

フィールドが `biogeochemical_auxiliary_fields` で呼び出されると、帯の合計である `PAR` という追加のフィールドも返されます。
