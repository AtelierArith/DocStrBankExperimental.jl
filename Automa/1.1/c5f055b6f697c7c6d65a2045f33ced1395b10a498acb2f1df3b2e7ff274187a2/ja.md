```
generate_code([::CodeGenContext], machine::Machine, actions=nothing)::Expr
```

`machine`のための初期化および実行コードを生成します。関数を作成するためのデフォルトのコード生成関数であり、便利さから直接初期化および実行コードを生成するよりも優先的に使用してください。次のコードを連結して生成するためのショートハンドです：

  * `generate_init_code(ctx, machine)`
  * `generate_action_code(ctx, machine, actions)`
  * `generate_input_error_code(ctx, machine)` [actions == :debugの場合は省略]

# 例

```
@eval function foo(data)
    # アクションで使用される変数を初期化
    data_buffer = UInt8[]
    $(generate_code(machine, actions))
    return data_buffer
end
```

参照： [`generate_init_code`](@ref), [`generate_exec_code`](@ref)
