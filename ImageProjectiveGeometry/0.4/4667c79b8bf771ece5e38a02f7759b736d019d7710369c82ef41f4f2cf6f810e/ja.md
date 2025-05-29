imdilate - 任意の構造要素を用いた2D形態学的膨張

```
Usage:   dimg = imdilate(img, se)

Arguments:
          img - 膨張される画像。グレースケールまたはバイナリである可能性があります
                ::Array{T,2} または ::BitArray{2}
           se - 2D Bool 配列で定義された構造要素

Returns:
         dimg - 膨張された画像
```

See also: imerode(), circularstruct()
