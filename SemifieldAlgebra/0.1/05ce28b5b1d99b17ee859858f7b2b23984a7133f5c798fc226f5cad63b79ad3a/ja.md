```
struct Semifield{T,A,M,MI,Z,O} <: Number
    val::T
end
```

`T` は値の型、`A` は加算関数、`M` は乗算関数、`MI` は乗算逆関数、`Z` はゼロ要素関数、`O` は一要素関数です。
