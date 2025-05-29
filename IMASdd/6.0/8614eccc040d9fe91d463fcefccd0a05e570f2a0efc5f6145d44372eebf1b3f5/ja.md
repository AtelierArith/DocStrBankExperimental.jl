```
isempty(@nospecialize(ids::IDS), field::Symbol; include_expr::Bool=false, eval_expr::Bool=false)
```

idsフィールドにデータ（または式）がない場合はtrueを返します

注意：デフォルトでは、式を含めず、評価もしません
