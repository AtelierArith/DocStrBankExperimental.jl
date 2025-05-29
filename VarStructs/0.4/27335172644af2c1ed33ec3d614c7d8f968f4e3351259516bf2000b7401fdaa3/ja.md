isunset(x)

フィールドの値がまだ設定されていない場合はtrueを返します。

# 例

```julia
mystruct = @var struct MyStruct
    x::Int64
end

isunset(mystruct.x) # true
```

```julia
isunset( Unset() ) # true
```
