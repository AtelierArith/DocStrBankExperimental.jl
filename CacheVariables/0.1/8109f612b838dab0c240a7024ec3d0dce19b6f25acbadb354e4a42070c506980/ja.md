```
cache(f, path; mod = @__MODULE__)
```

`f()`を実行して得られた出力を`path`にBSONファイルとしてキャッシュします。ファイルが存在する場合は読み込み、存在しない場合は実行して保存します。`mod`キーワード引数を使用してモジュールを指定します。

ヒント: `do...end`を使用してコードブロックの出力をキャッシュします。

# 例

```julia-repl
julia> cache("test.bson") do
         a = "計算に非常に時間がかかる量"
         b = "非常に長いシミュレーションを実行"
         return (; a = a, b = b)
       end
[ Info: Saving to test.bson
(a = "計算に非常に時間がかかる量", b = "非常に長いシミュレーションを実行")

julia> cache("test.bson") do
         a = "計算に非常に時間がかかる量"
         b = "非常に長いシミュレーションを実行"
         return (; a = a, b = b)
       end
[ Info: Loading from test.bson
(a = "計算に非常に時間がかかる量", b = "非常に長いシミュレーションを実行")
```
