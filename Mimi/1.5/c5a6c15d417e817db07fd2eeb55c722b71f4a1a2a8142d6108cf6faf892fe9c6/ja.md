```
replace_comp!(
    m::Model, comp_id::ComponentId, comp_name::Symbol=comp_id.comp_name;
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    reconnect::Bool=true
)
```

モデル `m` 内の名前 `comp_name` のコンポーネントを、`comp_id` で指定された新しいコンポーネントに置き換えるための非推奨関数です。代わりに次の構文を使用してください：

`replace!(m, comp_name => Mimi.compdef(comp_id); kwargs...)`

利用可能な機能のさらなる説明については、`replace!` のドキュメントを参照してください。
