```
AbstractConsumeContext
```

エンドユーザーはこれをサブタイプ化してカスタムコンシュームコンテキストを作成し、それを `parse_file_parallel` と `parse_file_serial` で使用して、`populate_result_buffer!` メソッドにディスパッチします。

# 参照:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref), [`populate_result_buffer!`](@ref)
  * 参照: [`consume!`](@ref), [`setup_tasks!`](@ref), [`setup_tasks!`](@ref), [`cleanup`](@ref), [`AbstractResultBuffer`](@ref)
