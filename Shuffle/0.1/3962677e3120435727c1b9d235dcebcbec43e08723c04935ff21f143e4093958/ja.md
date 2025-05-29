```
AbstractDeterministicShuffle <: AbstractShuffle
```

完全に決定論的なシャッフルアルゴリズムのスーパークラス、例えば [`Faro`](@ref) や [`Cut`](@ref) などです。

# 実装

新しい決定論的シャッフルアルゴリズムは、適切に [`shuffle`](@ref) または [`shuffle!`](@ref) のいずれかを実装する必要があります。新しいシャッフルメソッドは、最初の引数としてシャッフルされるコレクションを、2番目の引数として新しいシャッフルアルゴリズムタイプのインスタンスを取るべきです。

例えば：

```julia
struct MyShuffle <: AbstractDeterministicShuffle
    parameter
end

function shuffle(c::AbstractArray, s::MyShuffle, prealloc_out=similar(c))
    # シャッフルを行う

    return prealloc_out
end
```

出力を事前に割り当てることで、インプレースで書けないアルゴリズムのために効率的な [`nshuffle!`](@ref) 関数を書くことも容易になります。

参照： [`AbstractShuffle`](@ref)
