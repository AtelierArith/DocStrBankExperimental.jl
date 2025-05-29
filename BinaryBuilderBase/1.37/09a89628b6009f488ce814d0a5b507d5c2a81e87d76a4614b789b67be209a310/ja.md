```
temp_prefix(func::Function)
```

一時的なプレフィックスを作成し、ユーザー定義の関数にプレフィックスを渡して、ビルド/パッケージング操作を一時的なプレフィックス内で行い、すべての操作が終了した後にクリーンアップされるようにします。提供されたパスがすでに存在する場合は、削除されます。

使用例:

```
out_path = abspath("./libfoo")
temp_prefix() do p
    # <ビルドステップをここに挿入>

    # ビルドしたパッケージをtarballにする
    tarball_path, tarball_hash = package(p, out_path)
end
```
