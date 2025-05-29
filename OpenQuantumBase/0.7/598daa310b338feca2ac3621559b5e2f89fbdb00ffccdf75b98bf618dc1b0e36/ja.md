```
q_translate_state(h::String; normal=false)
```

量子状態の文字列表現をベクトルに変換します。キーワード引数 `normal` は出力ベクトルを正規化するかどうかを示します。（現在は '0' と '1' のみがサポートされています）

# 例

単一項:

```julia-repl
julia> q_translate_state("001")
8-element Array{Complex{Float64},1}:
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
```

複数項:

```julia-repl
julia> q_translate_state("(101)+(001)", normal=true)
8-element Array{Complex{Float64},1}:
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
```
