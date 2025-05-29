```
get_current_week(use_date::Bool = false)
```

NFLシーズンの現在または次の週を返します。デフォルトではスケジュールを使用しますが、`use_date=true`を渡すことで日付ベースのヒューリスティックに切り替えることができます。

# 例

```julia
julia>  # 日付を使用している場合; today() == "2024-09-15"

julia>get_current_week()
2
```
