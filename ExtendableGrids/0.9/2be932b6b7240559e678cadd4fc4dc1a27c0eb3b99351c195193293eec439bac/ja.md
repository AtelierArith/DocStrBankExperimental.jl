```
simplexgrid(X,Y; bregions=[1,2,3,4],cellregion=1)
```

座標配列から2Dグリッドを生成するコンストラクタです。

境界領域番号は反時計回りにカウントされます：

|  場所 |  番号 |
| ---:| ---:|
|   南 |   1 |
|   東 |   2 |
|   北 |   3 |
|   西 |   4 |

キーワード引数を使用すると、デフォルトの領域番号を上書きできます。
