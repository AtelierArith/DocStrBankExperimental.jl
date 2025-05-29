```
grid(
    rens::Union{AbstractVector,Tuple,NamedTuple};
    placeholder::Union{Nothing,AbstractRenderable} = nothing,
    placeholder_size::Union{Nothing,Tuple} = nothing,
    aspect::Union{Nothing,Number,NTuple} = nothing,
    layout::Union{Nothing,Tuple,Expr} = nothing,
    show_placeholder::Bool = false,
    pad::Union{Tuple,Integer} = 0,
    order::Symbol = :row,
)
```

# 説明

イテラブル（`AbstractVector`、`Tuple`、`NamedTuple`）からグリッドを構築します。

レンダラブルをレイアウトして、希望するアスペクト比またはレイアウト（行数、列数、または`nothing`で1つ空き）を持つグリッドを作成します。複雑なレイアウトはコンポジタ式を使用してサポートされています。

# 引数

`placeholder`: 空のグリッドコンポーネントのプレースホルダー。 `placeholder_size`: 自動プレースホルダーのサイズ。 `aspect`: 目標グリッドアスペクト比。 `layout`: タプル（行、列）最終サイズまたは複雑な式。 `show_placeholder`: プレースホルダーを表示/非表示にします。 `pad`: レイアウトコンポーネント間の追加パディング。 `order`: 行優先の入力反復のための`:row`（デフォルト）または列優先のための`:col`。
