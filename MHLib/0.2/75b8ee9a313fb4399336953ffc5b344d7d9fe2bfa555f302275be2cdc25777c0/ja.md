```
GVNS{TSolution <: Solution(solution, meths_ch, meths_li, meths_sh, 
    consider_initial_sol=false)
```

GVNSを作成します。

与えられた解に対して、指定された構築、局所改善、およびシェイキングメソッドを`Vector{MHMethod}`として提供するGVNSを作成します。`consider_initial_sol`がtrueの場合、与えられた解を有効な初期解として考慮します。そうでない場合は、初期化されていないと見なされます。
