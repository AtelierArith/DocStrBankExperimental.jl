```
time2pointing!(sstr::ScanningStrategy, time_s, beam_dir, polangle_rad, resultvec)
time2pointing(sstr::ScanningStrategy, time_s, beam_dir, polangle_rad)
```

ビームの指向方向を、`beam_dir`の方向に沿って計算します。検出器は、角度`polangle_rad`に沿った偏光に敏感です。結果は、`time2pointing!`の場合は`resultvec`に保存され、`time2pointing`の場合は戻り値となります。これは、以下のフィールドを含む6要素の配列です。

1. 空の点のコラティチュード（ラジアン単位）
2. 空の点の経度（ラジアン単位）
3. 空の参照系における偏光角
4. 正規化された指向ベクトルのX成分
5. Y成分
6. Z成分

フィールド#4、#5、#6は冗長であり、コラティチュード（フィールド#1）と経度（フィールド#2）から導出できます。これらは、コードがすでに計算しているため返されます。

ベクトル`beam_dir`と角度`polangle_rad`は、焦点面の参照系で表現する必要があります。`polangle_rad == 0`の場合、検出器は焦点面のx軸に沿った偏光を測定します。焦点面に対する法線方向はz軸に沿っているため、ボアサイトディレクタは`beam_dir = [0., 0., 1.]`となります。
