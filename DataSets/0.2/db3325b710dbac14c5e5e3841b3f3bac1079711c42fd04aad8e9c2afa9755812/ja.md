```
newfile(func)
newfile(func, ctx)
```

新しい一時的な `Blob` オブジェクトを作成します。これは後で `BlobTree` の永続的な場所に割り当てられる可能性があります。永続的な場所に割り当てられない場合、一時ファイルはガーベジコレクション中にクリーンアップされます。

# 例

```
tree[path"some/demo/path.txt"] = newfile() do io
    println(io, "Hi there!")
end
```
