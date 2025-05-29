```
rad(x::ThickNumber)
```

`x`の幅の半分。IEEE Std 1788-2015の表9.2で要求されています。

# デフォルト実装

デフォルトの実装は次のとおりです。

```
rad(x::ThickNumber) = wid(x)/2
```
