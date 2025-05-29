````
SFTPClient.walkdir(sftp::SFTP, root; topdown=true, follow_symlinks=false, onerror=throw)
ディレクトリのディレクトリツリーを歩くイテレータを返します。
イテレータは `(rootpath, dirs, files)` を含むタプルを返します。


# 例
```julia
for (root, dirs, files) in walkdir(sftp, ".")
    println("ディレクトリ: $root")
    for dir in dirs
        println(joinpath(root, dir)) # ディレクトリへのパス
    end
    println("ファイル: $root")
    for file in files
        println(joinpath(root, file)) # ファイルへのパス
    end
end
```
````
