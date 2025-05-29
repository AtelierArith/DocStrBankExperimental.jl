```
AbstractTransform
```

ImageNet前処理パイプラインの抽象型。期待されるインターフェース：

  * `transform(method, image_path)`: 画像を読み込み、WHC配列に変換する
  * `inverse_transform(method, array)`: WHC[N]配列を画像に変換する
