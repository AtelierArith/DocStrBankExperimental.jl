```
LNS(sol::Solution, meths_ch, meths_de, meths_re;
    meths_compat, consider_initial_sol, scheduler_params, 
    method_selector, params)
```

LNSを作成します。

与えられた解に対して、与えられた構築および修復メソッドを`Vector{MHMethod}`として提供するLNSを作成します。`consider_initial_sol`が真の場合、与えられた解を有効な初期解として考慮します。そうでない場合、それは初期化されていないと見なされます。
