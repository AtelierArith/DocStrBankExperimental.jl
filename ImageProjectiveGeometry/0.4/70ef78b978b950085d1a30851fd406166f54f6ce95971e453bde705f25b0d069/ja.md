imerode - 任意の構造要素を用いた2D形態学的侵食

```
Usage:   eimg = imerode(img, se)

Arguments:
          img - 侵食される画像。グレースケールまたはバイナリである可能性があります
                ::Array{T,2} または ::BitArray{2}
           se - 2D Bool配列で定義された構造要素

Returns:
         eimg - 侵食された画像
```

See also: imdilate(), circularstruct()
