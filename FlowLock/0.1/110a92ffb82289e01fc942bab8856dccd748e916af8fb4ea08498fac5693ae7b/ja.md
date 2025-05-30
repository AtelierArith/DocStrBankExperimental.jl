```
@flow path="path/to/file" expr
```

`path`にあるファイルが存在するかどうかをチェックし、変更されていない場合にのみ`expr`を実行するマクロです。最初の実行後、`path`と同じ名前のファイルを作成し、.hashサフィックスを付けて、sha256サムハッシュを書き込みます。

# 例

```jldoctest
julia> filePath, _ = mktemp();

julia> @flow path=filePath begin
           println("This should only show once")
           write(filePath, "some random text")
       end
This should only show once
64

julia> @flow path=filePath begin
           println("This should only show once")
           write(filePath, "some random text")
       end
```
