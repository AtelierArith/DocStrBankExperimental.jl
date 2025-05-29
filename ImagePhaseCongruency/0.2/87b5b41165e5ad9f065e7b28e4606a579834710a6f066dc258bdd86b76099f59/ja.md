NaNを指定した値で配列内に置き換えます。

```
使用法: (newimg, mask) = replacenan(img, defaultval=0)

引数:
   img        - NaN値を含む配列。
   defaultval - NaNを置き換えるためのデフォルト値。

返り値:
        newim - 埋められた画像、
        mask  - 元の画像の非NaN領域を示すブール画像。
```

参照: [`fillnan`](@ref)
