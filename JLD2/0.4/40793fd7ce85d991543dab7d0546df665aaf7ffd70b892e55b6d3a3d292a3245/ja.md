```
@save filename var1 [var2 ...]
@save filename {compress=true} var1 name2=var2
```

現在のスコープから1つ以上の変数 `var1,...` をJLD2ファイル `filename` に書き込みます。

対話的に使用する場合は、現在のモジュールのグローバルスコープ内のすべての変数を `@save filename` を使用して保存できます。より永続的なコードは、不要な変数を保存しないように明示的な形式を好むべきです。

# 例

文字列 `hello` と配列 `xs` をJLD2ファイル example.jld2 に保存するには：

```julia
hello = "world"
xs = [1,2,3]
@save "example.jld2" hello xs
```

保存コマンドにオプションを渡すには `{}` を使用します。

```julia
@save "example.jld2" {compress=true} hello xs
```

異なる名前で変数を保存するには、通常の代入構文を使用します。

```julia
@save "example.jld2" greeting=hello xarray = xs
```
