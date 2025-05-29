```
style = StreamIndexStyle(A)
```

`A`のストリーミング軸のインデックス付けのサポートの程度を示すトレイト。選択肢は[`IndexAny()`](@ref)と[`IndexIncremental()`](@ref)（時間軸の進行のみを許可する配列、例えばウェブカメラからのビデオストリーム）。デフォルト値は`IndexAny()`です。

これはインスタンスではなく型に特化すべきです。ストリーミングコンテナ`S`の場合、このトレイトは次のように定義できます。

```julia
StreamIndexStyle(::Type{P}, ::typeof(f!)) = IndexIncremental()
```

ここで`P = typeof(parent(S))`です。
