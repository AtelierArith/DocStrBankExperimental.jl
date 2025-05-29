```
allocate_buffer(width::Integer, height::Integer, img_type::ASI_IMG_TYPE)
```

カメラが書き込むための画像バッファを割り当てます。

# 引数:

```
width: 画像の幅
height: 画像の高さ
img_type: 次のいずれか
    -ASI_IMG_RAW8
    -ASI_IMG_Y8
    -ASI_IMG_RAW16
    -ASI_IMG_RAW24
```

# 戻り値:

```
適切な形状のゼロ初期化された配列。
```

# 例外:

```
サポートされていない画像タイプが指定された場合、ASIWrapperErrorが発生します。
```
