```
GribFile(f::Function, filename::AbstractString, mode="rb")
```

GRIBファイルを開き、`f`を実行した後に自動的に閉じます。`mode`は`Base.open`で説明されているモードです。

# 例

```julia
GribFile(filename) do f
    # 読み取りモードでの処理
end
```
