```
thres = yen_threshold(img)
thres = yen_threshold(img, bins)
```

グレースケール画像のための閾値を計算します。Yenの最大相関基準を使用して二値閾値処理を行います。

パラメータ:

  * img         = グレースケール入力画像
  * bins        = ヒストグラムを計算するために使用されるビンの数。浮動小数点画像に必要です。

#引用 Yen J.C., Chang F.J., and Chang S. (1995) “A New Criterion for Automatic Multilevel Thresholding” IEEE Trans. on Image Processing, 4(3): 370-378. DOI:10.1109/83.366472
