```
toDictValue!(dict, plan::RecoPlan)
```

`plan`のプロパティを`toDictValue`を使用して、欠損していない各フィールドに対して`dict`に追加します。さらに、各`listener::AbstractPlanListener`を`dict`に追加します。
