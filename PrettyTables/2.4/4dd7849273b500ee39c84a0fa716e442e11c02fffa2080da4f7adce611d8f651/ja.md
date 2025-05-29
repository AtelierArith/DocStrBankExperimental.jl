```
include_pt_in_file(filename::AbstractString, mark::AbstractString, args...; kwargs...) -> Nothing
```

`filename`に`mark`を使用してテーブルを含めます。

この関数は、引数`args`とキーワード`kwargs`を使用してテーブルを印刷します（**ここで`args`にIOを渡してはいけません**）。次に、ファイル`filename`内で以下のセクションを検索します：

```
<PrettyTables mark>
...
</PrettyTables>
```

そして、**マークの間のすべてを**印刷されたテーブルで**置き換えます**。閉じタグが別の行にある場合、その前のすべての文字は保持されます。これはコメントタグを追加するために重要です。

ユーザーが開閉タグを削除したい場合は、キーワード`remove_tags = true`を渡します。

キーワード`tag_append`は、開タグの後にテキストを追加するために使用できる文字列を渡すために使用できます。これは、コメントに開閉タグがあるHTMLにとって重要です。したがって、`tag_append = " -->"`の場合、次のようにHTMLファイルにテーブルを追加できます：

```
<!-- <PrettyTables mark> -->
...
<!-- </PrettyTables> -->
```

デフォルトでは、この関数は元のファイルを`filename_backup`にコピーします。これが望ましくない場合は、キーワード`backup_file = false`を関数に渡します。
