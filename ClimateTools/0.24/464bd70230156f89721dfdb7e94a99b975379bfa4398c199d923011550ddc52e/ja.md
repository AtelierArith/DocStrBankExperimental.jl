```
tropicalnights(C::ClimGrid)
```

TropicalNights、熱帯夜の数：TN（毎日の最高気温）が20度セルシウスを超える日の年間カウント。

TN[i,j]を年jのi日目の毎日の最低気温とします。次の条件を満たす日の数をカウントします：

TN[i,j] > 20セルシウス。
