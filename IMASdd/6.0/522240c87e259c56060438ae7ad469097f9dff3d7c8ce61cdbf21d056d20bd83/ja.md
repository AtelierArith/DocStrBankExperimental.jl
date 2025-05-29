```
isempty(@nospecialize(ids::IDS); include_expr::Bool=false, eval_expr::Bool=false)
```

IDSフィールドの下流にデータ（または式）がない場合はtrueを返します。

注意：デフォルトでは、式は含まれず、評価されません。
