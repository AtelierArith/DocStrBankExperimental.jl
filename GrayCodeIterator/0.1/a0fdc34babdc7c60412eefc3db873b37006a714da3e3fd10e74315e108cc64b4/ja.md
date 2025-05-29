```
GrayCode(n, k [, prefix, mutate = false])
```

長さ `n` および重み `k` のすべてのバイナリベクトルを提供するイテレータを作成します。オプションで、プレフィックスベクトルを提供することができます。イテレータのアイテムは `Vector{Int}` 型です。

`mutate = true` を設定すると、ベクトルがその場で変異します。これによりイテレーションが高速化される可能性がありますが、このオプションを使用する場合は、自分でベクトルを変更しないでください。`collect` が正しく機能するためには、`mutate` は `false`（デフォルト）でなければなりません。

# 例

```julia-repl
julia> collect(GrayCode(4,2))
6-element Vector{Vector{Int64}}:
 [0, 0, 1, 1]
 [0, 1, 1, 0]
 [0, 1, 0, 1]
 [1, 1, 0, 0]
 [1, 0, 1, 0]
 [1, 0, 0, 1]
```

```julia-repl
julia> collect(GrayCode(4,2,[1,0]))
2-element Vector{Vector{Int64}}:
 [1, 0, 0, 1]
 [1, 0, 1, 0]
```
