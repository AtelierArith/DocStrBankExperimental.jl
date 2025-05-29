```
set_default_arg_group!(settings, [name])
```

次の[`@add_arg_table!`](@ref)マクロおよび[`add_arg_table!`](@ref)関数の呼び出しに対するデフォルトグループを設定します。`name`は`String`であり、標準グループ名（`"command"`、`"positional"`または`"optional"`）のいずれか、または`add_arg_group!`で指定されたユーザー定義名のいずれかでなければなりません（名前が割り当てられていないグループはこの関数で使用できません）。

`name`が提供されない場合、または空の文字列`""`の場合、デフォルトの動作はリセットされます（つまり、引数は自動的に標準グループに割り当てられます）。`name`は`Symbol`としても渡すことができます。
