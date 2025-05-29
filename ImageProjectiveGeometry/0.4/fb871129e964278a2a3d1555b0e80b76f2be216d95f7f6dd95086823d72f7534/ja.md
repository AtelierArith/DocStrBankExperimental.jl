coherence - 構造テンソルから画像のコヒーレンスを計算する

```
Usage:      cimg = coherence(img, sigma=1)

Arguments:   
           img    - 処理する画像。
                    ::Array{T,2} または ::ImageMeta{T,2} 
           sigma  - ガウス合計ウィンドウの標準偏差。 
                    使用する典型的な値は1-3です。デフォルトは1です。
Returns:
           cimg   - コヒーレンス画像。
```

コヒーレンスは、構造テンソルの固有値の差を固有値の合計で割り、そのすべてを二乗したものとして定義されます。  

```
     ((L1-L2)./(L1+L2)).^2
```

小さい値は、固有値が大きさにおいて類似していることを示し、したがって局所構造が強い2D成分を持っていることを示します。

入力がImageMetaの場合、cimgはプロパティspatialorderが["y","x"]に設定されたImageMetaになります。

参照: structuretensor()
