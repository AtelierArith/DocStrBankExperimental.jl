nonmaxsuppts - 特徴/コーナーのための非最大抑制

特徴またはコーナー検出器によって生成されたポイントの非最大抑制としきい値処理。

```
Usage:   (r,c) = nonmaxsuppts(cimg; radius=1, thresh=0, N=Inf, subpix=false, img=[], fig=nothing)

Argument:
           cimg   - コーナー強度画像。 ::Array{T,2}

Keyword Arguments:
           radius - 非最大抑制で考慮される領域の半径。使用する典型的な値は1-3ピクセルです。デフォルト（および最小値）は1です。
           thresh - しきい値、しきい値を超える値を持つ特徴のみが返されます。デフォルトは0です。
                N - 返される最大特徴数。この場合、'thresh'を超えるN個の最も強い特徴が返されます。デフォルトはInfです。
         subpixel - trueに設定すると、特徴がサブピクセル精度で局所化されます。デフォルトはfalseです。
             img  - オプションの画像データ。画像が提供されると、検出されたコーナーがこの画像に重ねられます。これはパラメータ調整に役立ちます。デフォルトは[]です。
              fig - 画像とコーナーポイントを表示するためのオプションの図番号。指定されていない場合は新しい図が生成されます。

Returns:
           r,c    - コーナーポイントの行と列の座標。
```

使用例:

```
 > hes = hessianfeatures(img, 1)   # 画像imgにおけるヘッセ行列特徴画像を計算
```

非最大抑制半径2を使用してサブピクセル精度で最も強い1000の特徴を見つけ、検出されたコーナーを元の画像に重ねます。

```
 > (r,c) = nonmaxsuppts(abs(hes), radius=2, N=1000, img=img, subpixel=true)
```

注意: 整数値の画像に関する問題は、距離2*radius以内に同じ値を持つ複数のピクセルがある場合、それらすべてが局所最大としてマークされることです。

参照: harris(), noble(), shi_tomasi(), hessianfeatures()
