```
@jdiff [name] A B [clauses...] begin ... end
```

AとBの違いを分析します。

`name`が指定されていない場合、このコンテキストには現在アクティブなコンテキストとしてのみアクセスできます。

# 引数

  * `name`::String: このアクセラレータコンテキストの一意の名前
  * `A`, `B`::テストケース

# 例

```julia-repl
julia> @jdiff myacc fort_impl(USE_HIP=false) hip_impl(USE_HIP=true) begin
...
end
```

# 実装

T.B.D.
