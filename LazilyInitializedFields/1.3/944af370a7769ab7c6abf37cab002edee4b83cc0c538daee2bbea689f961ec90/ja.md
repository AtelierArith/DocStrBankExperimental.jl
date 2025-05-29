```
@lazy struct Foo
    a::Int
    @lazy b::Int
    @lazy c::Float64
end
```

`b`と`c`の遅延フィールドを持つ構造体`Foo`を作成します。
