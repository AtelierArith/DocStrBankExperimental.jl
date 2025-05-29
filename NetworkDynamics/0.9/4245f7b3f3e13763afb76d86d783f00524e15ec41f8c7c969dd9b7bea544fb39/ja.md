```
get_initial_state(c::ComponentModel, syms; missing_val=nothing)
get_initial_state(nw::Network, sni::SymbolicIndex; missing_val=nothing)
```

コンポーネントモデル `c` のシンボル `sym`（単一のシンボルまたはベクトル）の初期状態を返します。シンボルが初期化されていない場合は `missing_val` を返します。観測されたシンボルにも対応しています。

関連情報: [`dump_initial_state`](@ref).
