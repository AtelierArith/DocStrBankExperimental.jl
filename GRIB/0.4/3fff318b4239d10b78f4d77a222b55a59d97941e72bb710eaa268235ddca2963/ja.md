```
Index(f::Function, filename::AbstractString, keys...)
```

指定されたキーを持つファイルからインデックスを作成し、自動的にファイルを閉じます。

# 例

```Julia
Index(filename, "shortName", "level") do index
    # インデックスを使って処理を行う
end
```
