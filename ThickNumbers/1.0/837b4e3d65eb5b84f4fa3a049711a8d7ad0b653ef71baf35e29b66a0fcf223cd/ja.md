```
mid(x::ThickNumber)
```

`x`のスパンの中点。IEEE Std 1788-2015の表9.2で要求されています。

# デフォルト実装

デフォルトの実装は次のとおりです。

```
mid(x::ThickNumber) = (loval(x) + hival(x))/2
```
