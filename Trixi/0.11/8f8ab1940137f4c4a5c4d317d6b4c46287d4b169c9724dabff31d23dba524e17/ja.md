```
AMRCallback(semi, controller [,adaptor=AdaptorAMR(semi)];
            interval,
            adapt_initial_condition=true,
            adapt_initial_condition_only_refine=true,
            dynamic_load_balancing=true)
```

指定されたセミ離散化 `semi` に対して選択した `controller` を使用して、`interval` タイムステップごとに適応メッシュ細分化 (AMR) を実行します。
