```
generate_exec_code([::CodeGenContext], machine::Machine, actions=nothing)::Expr
```

アクションを伴うマシン実行コードを生成します。このコードは、マシンが`generate_init_code`で初期化された後に実行されるべきです。渡されない場合、コンテキストは`DefaultCodeGenContext`にデフォルト設定されます。

可能な限り、この関数の代わりにより一般的な`generate_code`を使用することをお勧めします。この関数は、実行コードの前に初期化されたデータを変更する必要がある場合に使用されるべきです。

# 例

```
@eval function foo(data)
    $(generate_init_code(machine))
    p = 2 # 位置2から始めたいかもしれない、1ではなく
    $(generate_exec_code(machine, actions))
    return cs
end
```

参照: [`generate_init_code`](@ref), [`generate_exec_code`](@ref)
