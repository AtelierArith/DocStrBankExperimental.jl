```
load_domain(domain::Symbol)
load_domain(collection::Symbol, domain)
```

デフォルトのリポジトリ（`PlanningDomains.JuliaPlannersRepo`）からドメインをロードします。`Symbol`内のアンダースコア '_' は自動的にダッシュ '-' に変換されます。
