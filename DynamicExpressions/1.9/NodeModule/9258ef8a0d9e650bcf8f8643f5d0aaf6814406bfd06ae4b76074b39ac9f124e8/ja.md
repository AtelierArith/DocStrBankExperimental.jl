```
GraphNode{T} <: AbstractExpressionNode{T}
```

[`Node{T}`](@ref) とまったく同じですが、一部のノードが共有されるという仮定があります。このグラフのような構造のすべてのコピーは、この仮定に基づいて行われ、グラフの構造を保持します。

# 例

```julia
julia> operators = OperatorEnum(;
           binary_operators=[+, -, *], unary_operators=[cos, sin]
        );

julia> x = GraphNode(feature=1)
x1

julia> y = sin(x) + x
sin(x1) + {x1}

julia> cos(y) * y
cos(sin(x1) + {x1}) * {(sin(x1) + {x1})}
```

`{}` がノードが共有されていることを示しており、これは文字列内で以前に見たのと同じノードです。

これは [`Node{T}`](@ref) と同じコンストラクタを持っています。共有ノードは、構築またはプロパティを設定する際に同じノードを複数の場所で使用することによって簡単に作成されます。
