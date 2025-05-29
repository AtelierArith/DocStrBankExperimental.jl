```julia
read_blocks(
    exo::Exodus.ExodusDatabase,
    block_ids::Union{Vector{<:Integer}, var"#s80"} where var"#s80"<:Integer
) -> Any

```

ブロックを初期化するためのヘルパーメソッド。

TODO: 名前をread*element*blocksに変更する
