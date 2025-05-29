```
blendimg!(color::GMTimage, shade::GMTimage; new=false, mode="", transparency=0.5, white=220, burn_up=180, screen_low=200)
```

`color` GMTimage（通常はRGB画像）を`shade`強度画像（通常はgdaldemまたはBlenderレイトレーサーで取得）とブレンドします。ただし、特定のブレンダーモードでは、$color$または$shade$の両方がRGBまたはグレースケール画像である可能性があります。「LinearBurn」と「Screen」モードを組み合わせて驚くべき「シェーディング効果」を作成する方法については、このYouTubeビデオを見ることを強くお勧めします。 https://somethingaboutmaps.wordpress.com/2014/10/26/adding-shaded-relief-in-photoshop/

  * `mode`:

      * `mode=""`または`mode="gcalc"`: ブレンド方法は、https://gis.stackexchange.com/questions/255537/merging-hillshade-dem-data-into-color-relief-single-geotiff-with-qgis-and-gdal/255574#255574 で説明されているものです。
      * `mode="blend"`: 単純な50%（デフォルト）ブレンドが行われます。`transparency`を]0 1[の範囲内の他の値に設定すると、画像の一方に重みを付けることができます。0.75は`img`が合計の3/4の重みを持つようにします。
      * `mode="LinearBurn"`: （Photoshopブレンダー*LinearBurn*と同じ）上層と下層のピクセル値を加算し、255を引きます。画像を暗くする傾向があります。`burn_up`オプションは、$shade$のしきい値を設定し、その値を超えると$color$画像は変更されません。
      * `mode="ColorBurn"`: （Photoshopブレンダー*ColorBurn*と同じ）$color$レイヤーのピクセル値を反転させ、それを$shade$のピクセル値で割り、結果を再度反転させます。画像を暗くする傾向があります。
      * `mode="Screen"`: （Photoshopブレンダー*Screen*と同じ）2つの画像の可視ピクセルの値を反転させます。（つまり、それぞれを255から引きます）次に、それらを掛け合わせ、再度この値を反転させます。結果の画像は通常明るく、時には「洗い流された」ように見えます。この洗い流し効果を制御するには、$shade$のしきい値を設定する`screen_low`オプションを使用します。この値は非常にケース依存であり、通常は適切な値を見つけるために試行錯誤が必要です。洗い流し効果を制御する別の方法は、255とは異なる`white`オプションを使用することです。ここでのデフォルトは`white=220`で、追加された明るさを少し抑えます。
  * `new`: trueの場合は新しいGMTimageオブジェクトを返し、そうでない場合は`color`の内容を変更します。
