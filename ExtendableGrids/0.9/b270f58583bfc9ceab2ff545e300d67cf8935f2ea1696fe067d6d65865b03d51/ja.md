```
simplexgrid(X,Y,Z; bregions=[1,2,3,4,5,6],cellregion=1)
```

座標配列から3Dグリッドを生成するコンストラクタ。境界領域番号:

| location | number |
| --------:| ------:|
|    south |      1 |
|     east |      2 |
|    north |      3 |
|     west |      4 |
|   bottom |      5 |
|      top |      6 |

キーワード引数を使用すると、デフォルトの領域番号を上書きできます。
