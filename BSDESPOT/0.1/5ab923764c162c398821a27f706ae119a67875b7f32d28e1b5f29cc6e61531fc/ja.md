```
IndependentBounds(lower, upper, check_terminal=false, consistency_fix_thresh=0.0)
```

互いに独立した下限と上限を指定します（最も一般的なケース）。

# キーワード引数

  * `check_terminal::Bool=false`: trueの場合、信念内のすべての状態が終端である場合、上限と下限は上書きされて0に設定されます。
  * `consistency_fix_thresh::Float64=0.0`: `upper < lower` かつ `upper >= lower-consistency_fix_thresh` の場合、`upper` は `lower` に引き上げられます。
