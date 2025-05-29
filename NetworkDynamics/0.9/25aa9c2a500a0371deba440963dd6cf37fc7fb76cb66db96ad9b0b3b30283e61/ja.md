```
add_callback!(c::ComponentModel, cb; check=true)
add_callback!(nw::Network, idx::Union{VIndex,EIndex}, cb; check=true)
```

コンポーネントにコールバック関数を追加します。既存のコールバックは上書きされません。詳細は[`set_callback!`](@ref)を参照してください。
