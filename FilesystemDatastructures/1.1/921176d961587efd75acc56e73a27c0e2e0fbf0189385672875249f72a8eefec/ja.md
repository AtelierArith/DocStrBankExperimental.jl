```
NFileCache <: FileCache
```

ファイル数制約のあるファイルキャッシュを表します。キャッシュ内の最大ファイル数と、どの要素を破棄するかを選択する方法を設定できます。

```
NFileCache(root, nfiles, discard_func; predicate=x->true)
```

新しいファイルキャッシュを構築します。引数:

  * `root`: キャッシュのルートディレクトリ。
  * `nfiles`: 保持するファイルの数。
  * `discard_func`: 追放順序を返す関数。例として `DiscardLRU` や `DiscardLFU` を参照してください。
  * `predicate`: ファイルが追跡/キャッシュに含まれるべきかを決定する関数。現在、ファイルキャッシュを設定する際に既存のファイルにのみ使用されます。デフォルトは、すべての既存ファイルを追跡することです。

!!! warn
    これは潜在的に破壊的な操作です。なぜなら、ファイルキャッシュは与えられた制約に収めるために `root` ディレクトリ内のファイルを削除する可能性があるからです。


使用例:

```
# 最大10ファイルを保持し、LRUオブジェクトを解放するキャッシュを作成
fc = NFileCache(root, 10, DiscardLRU())

# 新しいファイルを追加:
path = add!(fc, key)
open(path, "w") do io
    write(path, filedata)
end

# そのファイルが存在するか確認する（使用カウンタも増加させる）
hit!(fc, key)

# そのファイルを削除
delete!(fc, key)
```
