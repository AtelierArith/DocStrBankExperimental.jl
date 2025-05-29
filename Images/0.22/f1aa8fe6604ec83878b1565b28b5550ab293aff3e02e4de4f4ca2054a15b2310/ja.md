```
thres = otsu_threshold(img)
thres = otsu_threshold(img, bins)
```

Otsuの手法を使用してグレースケール画像のしきい値を計算します。

パラメータ：

  * img         = グレースケール入力画像
  * bins        = ヒストグラムを計算するために使用されるビンの数。浮動小数点画像に必要です。
