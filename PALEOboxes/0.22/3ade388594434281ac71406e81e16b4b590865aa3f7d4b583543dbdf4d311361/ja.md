```
show_variables(model::Model; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
show_variables(model::Model, domainname; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
```

ドメイン変数のテーブルを表示します。オプションで変数リンクやデータを取得します。

# キーワード:

[`show_variables(domain::Domain, kwargs...)`](@ref) を参照してください。

# 例:

VS Codeのテーブルビューアを使用してすべてのモデル変数を表示します:

```
julia> vscodedisplay(PB.show_variables(run.model))
```

スプレッドシートにインポートするためにすべてのモデル変数をcsvとして書き出します:

```
julia> CSV.write("vars.csv", PB.show_variables(run.model, modeldata=modeldata, showlinks=true))
```
