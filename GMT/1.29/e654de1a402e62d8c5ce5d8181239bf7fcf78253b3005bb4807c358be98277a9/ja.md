```
I = grays2rgb(bandR, bandG, bandB, GI=nothing) -> GMTimage
```

3つのグレースケール画像をUInt8行列またはGMTimageとして受け取り、各バンドの値を出力画像のそれぞれのカラー チャンネルに単純にコピーすることでRGB画像を構成します。入力がUInt8行列の場合、出力の地理参照情報を設定するために、オプションでGMTgridまたはGMTimageを4番目の引数として提供します。出力は常にGMTimageオブジェクトです。

この関数を、単一のインデックス画像を受け取り、その画像のカラーマップを使用してRGBを作成する`ind2rgb`と混同しないでください。

### 例

```juliadoc
I1 = mat2img(rand(UInt8, 16,16)); I2 = mat2img(rand(UInt8, 16,16)); I3 = mat2img(rand(UInt8, 16,16));
Irgb = grays2rgb(I1,I2,I3)
```
