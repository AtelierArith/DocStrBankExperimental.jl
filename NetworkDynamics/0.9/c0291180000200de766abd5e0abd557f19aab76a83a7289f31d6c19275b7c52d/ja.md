```
set_callback!(c::ComponentModel, cb; check=true)
set_callback!(nw::Network, idx::Union{VIndex,EIndex}, cb; check=true)
```

コンポーネントのコールバック関数を設定します。既存のコールバックは上書きされます。詳細は[`add_callback!`](@ref)を参照してください。
