```
delete_preferences!(uuid_or_module_or_name, prefs::String...;
                    block_inheritance::Bool = false, export_prefs=false, force=false)
```

指定された uuid::UUID/module::Module/name::String に対して、一連の設定を削除します。これは、`prefs` として渡されたキーによって識別されます。

詳細については、[`set_preferences!`](@ref) のドキュメントを参照してください。
