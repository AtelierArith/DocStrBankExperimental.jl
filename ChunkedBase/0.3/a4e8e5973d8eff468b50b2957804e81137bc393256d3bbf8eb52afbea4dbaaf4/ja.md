```
AbstractParsingContext
```

ユーザーはこれをサブタイプ化してカスタムパースコンテキスト変数を作成し、それを `parse_file_parallel` / `parse_file_serial` で使用して、`populate_result_buffer!` メソッドにディスパッチします。

# 参照:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref), [`populate_result_buffer!`](@ref)
