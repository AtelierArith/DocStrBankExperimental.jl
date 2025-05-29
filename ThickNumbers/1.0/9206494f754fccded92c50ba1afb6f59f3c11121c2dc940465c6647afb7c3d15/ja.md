```
wid(x::ThickNumber)
```

`x`のスパンの幅。IEEE Std 1788-2015の表9.2で要求されています。

# デフォルト実装

デフォルトの実装は次のとおりです。

```
wid(x::ThickNumber) = hival(x) - loval(x)
```
