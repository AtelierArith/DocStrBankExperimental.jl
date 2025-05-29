fitplanedemo - RANSAC平面フィッティングのデモ

関数は、外れ値を含むノイズの多いデータポイントのセットを生成し、RANSACを使用して平面をフィットさせます。

```
Usage: fitplanedemo(outliers, sigma, t, feedback)

Arguments:
              outliers - 外れ値となるポイントの割合を指定します。
              sigma    - 真の平面からの内点の標準偏差。
              t        - ポイントが内点であるかどうかを決定するためにRANSACアルゴリズムで使用される距離の閾値。
              feedback - RANSACフィードバック情報をオンにするためのオプションのフラグ0または1。

Try using:  fitplanedemo(0.3, 0.02, 0.05)
```

See also: ransacfitplane(), fitplane()
