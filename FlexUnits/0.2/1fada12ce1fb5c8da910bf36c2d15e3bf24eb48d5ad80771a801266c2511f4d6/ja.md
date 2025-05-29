```
NoDims{P}
```

単位のない次元で、他のどの次元とも互換性があります。

`getproperty`を呼び出すと、常に`zero(P)`が返されます。`promote(Type{<:NoDims}, D<:AbstractDimension)`はDを返します。`convert(Type{D}, NoDims)`はD<:AbstractDimensionsに対してD()を返します。
