```
UnsafeArray{T,N} <: DenseArray{T,N}
```

`UnsafeArray`は、メモリポインタとサイズタプルのビットタイプラッパーです。これは、`unsafe_wrap`によって返される`Array`や、`view`によって返される`SubArray`の短命で割り当て不要な代替品として使用されることを意図しています。使用には注意が必要です！

コンストラクタ:

```
UnsafeArray{T,N}(pointer::Ptr{T}, size::NTuple{N,Int}) where {T,N}
UnsafeArray(pointer::Ptr{T}, size::NTuple{N,Int}) where {T,N}
```

`UnsafeArray`は`isbitstype(T) == true`を要求します。

注意: 空の多次元`UnsafeArray`を構築することは安全です:

```
UnsafeArray(Ptr{Int}(0), (0,...))
```

注意: `U`が使用されている間に、`A`がガーベジコレクトされたり、`resize!`、`sizehint!`などを介して再割り当てされないことを*必ず*確認してください！`A`と`U`のライフサイクルを完全に制御できる状況でのみ使用してください。

`deepcopy(::UnsafeArray)`は標準の`Array`を返します。
