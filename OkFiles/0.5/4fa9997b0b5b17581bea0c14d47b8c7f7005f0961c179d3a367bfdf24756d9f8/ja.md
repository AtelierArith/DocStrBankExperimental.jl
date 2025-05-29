`mv2dir(f::Function, srcfile, newdir::AbstractString)` はファイル `srcfile` をディレクトリ `newdir` に移動します。`srcfile` の新しいパスは `newpath = joinpath(newdir, basename(srcfile)) |> f` であり、任意の関数 `f` を `newpath` に適用できます。

`mv2dir` は `mv` のキーワード引数を取ります。

# 例

`mkdirway(newpath)` はファイル `newpath` への道に沿ってディレクトリを作成します：

```julia
mv2dir(mkdirway, "hello/world/iris.csv", "another/world") # 結果は "another/world/iris.csv"
```

これは次のように等価です：

```julia
mkpath("another/world")
mv2dir("hello/world/iris.csv", "another/world") # 結果は "another/world/iris.csv"
```

もし `srcfile` がディレクトリの場合、

```julia
mkpath("another") # "another/world" は作成されないことに注意
mv2dir("hello/world", "another") # "world" の下のすべての内容を新しいフォルダ "another" に移動し、結果は "another/world/iris.csv"
```

これは次のように等価です：

```julia
mv2dir(mkdirway, "hello/world", "another") # 結果は "another/world/iris.csv"
```

また、`mkdirway` のドキュメントも参照してください。

# 別の例

`f = pathnorepeat` を適用できます：

```julia
mv2dir(pathnorepeat, "hello/world", "another") # ディレクトリ "another/world" がすでに存在する場合、結果は "another/world_0001/iris.csv"

mv2dir(pathnorepeat, "hello/world/iris.csv", "another/world") # ファイル "another/world/iris.csv" がすでに存在する場合、結果は "another/world/iris_0001.csv"
```
