```
similar_library(lib::Library, d::FullDim, T::Type)
```

全次元 `T` の多面体をサポートするライブラリを返します。係数型は `T` です。もし `lib` がそれをサポートしていない場合、通常は `default_library(d, T)` が呼び出されます。
