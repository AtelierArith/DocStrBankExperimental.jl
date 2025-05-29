```
ArraySize
```

は、配列サイズを定義するための型の和集合です。引数 `dims` が `isa(dims,ArraySize)` が真である任意のものである場合に `as_array_size(dims)` を呼び出すと、標準形の配列サイズ、すなわち `Int` の `N`-タプルのエイリアスである `Dims{N}` のインスタンスが得られます。
