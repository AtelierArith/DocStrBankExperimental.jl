```
unmarshal(T, dict[, verbose[, verboselvl]])
```

`JSON.parse` または現在の 'LazyJSON.parse' の辞書出力を使用して、タイプ T のオブジェクトを再構築します。

verbose を `true` に設定すると、データ階層がどのようにアンマーシャルされるかについてのデバッグ情報が得られます。これは、パースエラーや JSON オブジェクトとタイプ定義の不一致を追跡するのに役立つかもしれません。

# 例

```jldoctest
julia> using JSON

julia> var = randn(Float64, 5);  # 考えられる他のタイプのバリエーションでも動作するはずです

julia> unmarshal(typeof(var), JSON.parse(JSON.json(var)) ) == var
true
 
または 

julia> using LazyJSON

julia> var = randn(Float64, 5);  # 考えられる他のタイプのバリエーションでも動作するはずです

julia> unmarshal(typeof(var), LazyJSON.parse(JSON.json(var)) ) == var
true
```
