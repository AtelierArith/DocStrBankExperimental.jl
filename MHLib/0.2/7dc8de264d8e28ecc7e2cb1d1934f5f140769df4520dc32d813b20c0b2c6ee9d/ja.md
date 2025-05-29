```
ALNS(sol::Solution, meths_ch, meths_de, meths_re; 
    meths_compat, consider_initial_sol, scheduler_params, lns_params, alns_params)
```

適応的大規模近傍探索（ALNS）を作成します。

与えられた解に対して、与えられた構築および修復メソッドを`Vector{MHMethod}`として提供する`ALNSMethodSelector`を使用したLNS、すなわちALNSを作成します。`consider*initial*sol`が真の場合、与えられた解を有効な初期解として考慮します。そうでない場合は、初期化されていないと見なされます。
