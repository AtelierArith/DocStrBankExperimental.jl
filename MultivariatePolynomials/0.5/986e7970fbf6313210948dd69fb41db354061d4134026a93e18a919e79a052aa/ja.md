```
struct LazyMap{T, VT}
    f::Function
    data::VT
end
```

`f`によってマッピングされた`data`の要素を反復処理します。これは`Base.Generator(f, data)`に似ていますが、`LazyMap`の`eltype`は構築時に指定されるのに対し、`Base.Generator(f, data)`の`eltype`は`Any`です。
