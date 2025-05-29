```
noautorun(handlers...)::Function
```

指定されたすべてのハンドラータイプをオートラン内でスキップするために使用できるラッパー関数を構築します。

## 例

```julia
@syntax_eff noautorun(Vector, Identity) begin
  a = [1,2,3]
  b = Identity(a + 2)
end
```

これは、両方のハンドラーが無視するようにマークされているため、暗黙のオートランで実際にはハンドラーがまったく実行されないことを意味します。
