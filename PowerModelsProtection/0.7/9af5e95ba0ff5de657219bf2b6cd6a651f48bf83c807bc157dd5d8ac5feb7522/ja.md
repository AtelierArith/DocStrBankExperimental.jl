```
add_ct(data::Dict{String,Any}, element::String, id::String, n_p::Number, n_s::Number;kwargs...)
```

回路に電流トランスを追加するための関数。最初のCTを追加する場合は4、そうでない場合は5を入力します:     (1) data(Dictionary): parse*file()からの結果。回路情報     (2) element(String): CTが追加される要素またはライン     (3) id(String): オプション。同じラインに複数のCTがある場合。使用しない場合は以前に定義されたCT1を上書きします     (4) n*p(Number): プライマリ。トランスのリレー側の数になります     (5) n_s(Number): セカンダリ。ライン側の数     (6) kwargs: ユーザーが追加したいその他の情報。何にも使用されません。
