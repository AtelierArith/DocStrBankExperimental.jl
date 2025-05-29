```
add_callback!(simulation, callback::Callback; name = GenericName(), callback_kw...)

add_callback!(simulation, func, schedule=IterationInterval(1); name = GenericName(), callback_kw...)
```

`Callback(func, schedule)`を`simulation.callbacks`に`name`の下で追加します。デフォルトの`GenericName()`は、`N`が名前を一意にするのに十分な大きさの形`:callbackN`の名前を生成します。

`name::Symbol`が提供されると、`simulation.callbacks[name]`がすでに存在する場合は変更される可能性があります。

`callback_kw`は[`Callback`](@ref)のコンストラクタに渡されます。

スケジュールを含む`callback`も直接提供できます。
