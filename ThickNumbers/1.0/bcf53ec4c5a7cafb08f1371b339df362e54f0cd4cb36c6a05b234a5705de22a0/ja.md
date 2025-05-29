```
mag(x::ThickNumber)
```

`x`の最大絶対値。IEEE Std 1788-2015の表9.2で要求されています。

# デフォルト実装

デフォルトの実装は次のとおりです。

```
mag(x::ThickNumber) = max(abs(loval(x)), abs(hival(x)))
```
