```
codegen_match(f, x[, line::LineNumberNode=LineNumberNode(0), mod::Module=Main])
```

MLStyle コードジェネレーターを使用してゼロ依存のマッチ式を生成します。構文は MLStyle と同じです。

!!! tip
    `codegen_match` は MLStyle のパターンマッチング機能に依存しているため、ExproniconLite では使用できません。


# 例

```julia
codegen_match(:x) do
    quote
        1 => true
        2 => false
        _ => nothing
    end
end
```

このコードは、次の対応する MLStyle 式を生成します。

```julia
@match x begin
    1 => true
    2 => false
    _ => nothing
end
```
