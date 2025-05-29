```
Unset
```

まだ設定されていないときの VarStruct フィールドの値。

# 例

```julia
mystruct = @var struct MyStruct
    x::Int64
end

typeof(mystruct.x) # Unset

```
