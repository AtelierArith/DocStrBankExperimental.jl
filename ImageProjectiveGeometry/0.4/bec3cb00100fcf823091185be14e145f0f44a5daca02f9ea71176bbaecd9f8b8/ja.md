fitlinedemo - RANSAC直線フィッティングのデモ。

関数は、外れ値を含むノイズの多いデータポイントのセットを生成し、RANSACを使用して直線をフィットさせます。

```
Usage: fitlinedemo(outliers, sigma, t, feedback=false)

Arguments:
              outliers - 外れ値となるポイントの割合を指定します。
              sigma    - 真の直線からの内点の標準偏差。
              t        - RANSACアルゴリズムがポイントが内点であるかどうかを決定するために使用する距離の閾値。
              feedback - RANSACフィードバック情報をオンにするオプションのブールフラグ。

Try using:  fitlinedemo(0.3, 0.05, 0.05)
```

See also: ransacfitplane(), fitplane()
