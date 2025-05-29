```
@searchmethods x
@searchmethods ::X
```

`methodswith(typeof(x))` または `methodswith(X)` を対話的に検索します。

# 例

```julia
@searchmethods 1         # 整数に対して定義されたメソッドを検索
@searchmethods ::Int     # 指定された型に対して定義されたメソッドを検索
```
