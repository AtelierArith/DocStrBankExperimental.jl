```
@cache path code [overwrite]
```

`code`を実行して得られた結果を`path`にBSONファイルとしてキャッシュします。ファイルが存在する場合は読み込み、存在しない場合は実行して保存します。`overwrite`がtrueの場合は、どちらにしても実行して保存します（デフォルトはfalseです）。

ヒント: `code`のために`begin...end`を使用してコードブロックをキャッシュしてください。

注意: 変数名`ans`は最終出力を保存するために使用されるため、`code`内で変数名として使用しない方が良いです。

# 例

```julia-repl
julia> @cache "test.bson" begin
         a = "計算に非常に時間がかかる量"
         b = "非常に長いシミュレーションを実行"
         100
       end
┌ Info: test.bsonに保存中
│ a
└ b
100

julia> @cache "test.bson" begin
         a = "計算に非常に時間がかかる量"
         b = "非常に長いシミュレーションを実行"
         100
       end
┌ Info: test.bsonから読み込み中
│ a
└ b
100

julia> @cache "test.bson" begin
         a = "計算に非常に時間がかかる量"
         b = "非常に長いシミュレーションを実行"
         100
       end true
┌ Info: test.bsonを上書き中
│ a
└ b
100
```
