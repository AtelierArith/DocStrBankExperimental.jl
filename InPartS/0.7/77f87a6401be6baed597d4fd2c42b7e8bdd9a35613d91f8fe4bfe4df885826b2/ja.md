```
SimpleRegistrar{T<:Integer}(; next_id = one(T))
SimpleRegistrar() = SimpleRegistrar{UInt64}()
```

`T`の型の連続した番号を返すシンプルなレジストラで、[`set_id!`](@ref)/[`get_id!`](@ref)を呼び出すとデフォルトで`UInt64`になります。それ以外のことは何もしません。
