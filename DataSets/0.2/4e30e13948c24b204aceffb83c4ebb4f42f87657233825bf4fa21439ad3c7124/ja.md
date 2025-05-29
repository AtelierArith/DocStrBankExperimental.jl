```
dataset(name)
dataset(project, name)
```

指定された `name` を持つ [`DataSet`](@ref) を `project` から返します。省略した場合、グローバルデータ環境 [`DataSets.PROJECT`](@ref) が使用されます。

`DataSet` は *メタデータ* ですが、プログラムで実際の *データ* を使用するには、`open` 関数を使用して `DataSet` の内容にアクセスする必要があります。

# 例

`"a_text_file"` という名前のデータセットを開き、全内容を String として読み取るには、

```julia
content = open(String, dataset("a_text_file"))
```

同じデータセットを `IO` ストリームとして開き、最初の行だけを読み取るには、

```julia
open(IO, dataset("a_text_file")) do io
    line = readline(io)
    @info "The first line is" line
end
```

ディレクトリをブラウズ可能なツリーオブジェクトとして開くには、

```julia
open(BlobTree, dataset("a_tree_example"))
```
