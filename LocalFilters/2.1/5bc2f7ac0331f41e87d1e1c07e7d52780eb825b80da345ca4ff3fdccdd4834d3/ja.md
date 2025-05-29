```
const LocalFilters.Box{N} = FastUniformArray{Bool,N,true}
```

は、均一に `true` な `N` 次元配列の型へのエイリアスです。この種のインスタンスは、`LocalFilters` におけるハイパー長方形スライディングウィンドウを表すために使用されます。

メソッド [`LocalFilters.box`](@ref) を使用して、この型のオブジェクトを構築することができます。
