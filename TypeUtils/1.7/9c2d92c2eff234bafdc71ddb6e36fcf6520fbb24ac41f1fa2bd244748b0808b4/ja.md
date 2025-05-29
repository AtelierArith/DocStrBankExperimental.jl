```
c = TypeUtils.Converter(f, T::Type)
```

は、軽量な呼び出し可能オブジェクト `c` を構築します。これにより、任意の `x` に対して `c(x)` は `f(T, x)` を返します。Converter オブジェクトは、関数 `f` による型 `T` への変換をコレクションにマッピングするのに適しています。

これは `Base.Fix1(f,T)` に似ていますが、`sizeof(Base.Fix1(f,T)) = sizeof(Int)` であるのに対し、`sizeof(TypeUtils.Converter(f,T)) = 0` です。
