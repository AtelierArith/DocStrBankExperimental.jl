hessianfeatures  - 画像のヘッセ行列の行列式を計算します。

```
Usage: hdet = hessianfeatures(img, sigma)

Arguments:
            img      - 処理するグレースケール画像。
                       ::Array{T,2} または ::ImageMeta{T,2} 
            sigma    - スムージングスケールを定義します。

Returns:    hdet     - ヘッセ行列の行列式の行列
```

hdetの局所最大値は、暗いまたは明るいブロブの中心を示す傾向があります。ただし、局所化される点はスケールに依存する可能性があります。検出したいブロブが大きい場合は、同程度の大きさのsigmaの値を使用する必要があります。

hdetの局所最小値は、カメラキャリブレーションチェッカーボードパターンの交点を示すのに役立ちます。これらの鞍点特徴は、スケールの変動に対してより安定しているようです。

例えば、画像`img`の中で最も強い100の鞍点特徴を取得するには、次のようにします：

```
 > hdet = hessianfeatures(img, 1)      # sigma = 1
 > (r, c) = nonmaxsuppts(-hdet, N=100)
```

入力がImageMetaの場合、cimgはプロパティspatialorderが["y","x"]に設定されたImageMetaになります。

参照：harris(), noble(), shi_tomasi(), derivative5(), nonmaxsuppts()
