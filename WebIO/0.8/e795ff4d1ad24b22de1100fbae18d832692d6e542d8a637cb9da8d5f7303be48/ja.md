```
setup_provider(s::Union{Symbol, AbstractString})
```

指定されたプロバイダーを設定するために必要な副作用を実行します。たとえば、IJuliaでは、これによりフロントエンドがwebioのJavaScriptバンドルをロードします。
