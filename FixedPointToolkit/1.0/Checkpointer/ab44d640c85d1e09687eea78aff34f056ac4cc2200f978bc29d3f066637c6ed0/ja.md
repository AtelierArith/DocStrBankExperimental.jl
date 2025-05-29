```julia
save_checkpoint(fileName::String, sc::SelfCons, SelfConsParams::Dict{Symbol, Real})
```

`SelfCons`データ構造の関連属性をJLD2ファイル`fileName`に保存します（`fileName`は.jld2で終わる必要があります）。また、最大反復回数、許容誤差などの自己一貫性パラメータも保存します。
