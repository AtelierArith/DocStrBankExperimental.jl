```
SizeConstrainedFileCache <: FileCache
```

サイズ制約のあるファイルキャッシュを表します。キャッシュから要素を破棄するタイミングや、どの要素を破棄するかを選択するための異なるポリシーで構成可能です。

```
SizeConstrainedFileCache(root, target_func, discard_func; predicate=x->true)
```

新しいファイルキャッシュを構築します。引数：

  * `root`: キャッシュのルートディレクトリ。
  * `target_func`: キャッシュ内のファイルが占有できる（最大）バイト数を返す関数。例えば、`TargetSizeKeepFree`や`TargetSizeConstant`を参照してください。
  * `discard_func`: 追放順序を返す関数。例えば、`DiscardLRU`や`DiscardLFU`を参照してください。
  * `predicate`: ファイルがキャッシュに追跡/含まれるべきかを決定する関数。現在、ファイルキャッシュを設定する際に既存のファイルにのみ使用されます。デフォルトは、すべての既存ファイルを追跡することです。

!!! warn
    これは潜在的に破壊的な操作であり、ファイルキャッシュは与えられた制約に収まるように`root`ディレクトリ内のファイルを削除する可能性があります。


使用例：

```
# 10GBの空き容量を保持し、LRUオブジェクトを解放するキャッシュを作成
scfc = SizeConstrainedFileCache(root, TargetSizeKeepFree(10*1024^3), DiscardLRU())

# 新しいファイルを追加：
path = add!(scfc, key, filesize)
open(path, "w") do io
    write(path, filedata)
end

# そのファイルが存在するか確認（使用カウンタも増加させる）
hit!(scfc, key)

# そのファイルを削除
delete!(scfc, key)
```
