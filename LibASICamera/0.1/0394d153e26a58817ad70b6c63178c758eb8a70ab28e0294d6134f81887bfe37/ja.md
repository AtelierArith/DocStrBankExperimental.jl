```
set_roi_format(id::Integer, width, height, binning, img_type::ASI_IMG_TYPE)
```

領域の設定 (roi) を行います。キャプチャの前に行ってください。

幅と高さはバイニング後の値であり、つまり、640x480 @ BIN2 で動作させたい場合は、幅を640、高さを480に設定する必要があります。

ASI120のデータサイズは1024の倍数でなければならず、つまり width*height%1024==0 です。

# 引数:

```
id: カメラID
width: ROIの幅
height: ROIの高さ
binning: バイニングモード; 2は2x2ピクセルを一緒に読み出すことを意味します。どのバイニング値がカメラ構造体の ASI_CAMERA_INFO 構造体でサポートされているか、または get_camera_property(id) を呼び出すことで確認してください。
```

# 例外:

```
ASIError
```
