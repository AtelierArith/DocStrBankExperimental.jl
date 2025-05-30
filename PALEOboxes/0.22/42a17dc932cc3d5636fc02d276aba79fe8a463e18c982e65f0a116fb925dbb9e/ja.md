```
get_domain(model::Model, name::AbstractString; allow_not_found=true) -> Domain or nothing
get_domain(model::Model, domainid) -> Domain
```

`name` によってドメインを取得します（`name` が一致しない場合は何もない可能性があります）または `domainid`（範囲 1:num_domains）。
