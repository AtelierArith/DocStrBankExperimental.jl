```
@add_reactions
```

既存の [`ReactionSystem`](@ref) に宣言された反応を追加します。元のネットワークを変更することに注意してください。

ノート：

  * 代わりに、2つの既存のネットワークを組み合わせて新しいネットワークを生成するには `ModelingToolkit.extend` を使用します。

例：

```julia
rn = @reaction_network begin
    @parameters G
    π, 2*A --> B
    end

# この反応を rn に追加
@add_reactions rn begin
    k*A, C --> D
end
```
