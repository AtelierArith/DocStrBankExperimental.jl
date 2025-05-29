```
compare_aggregated_LOB_measurements(X::JMatrix{Float64}, Y::JMatrix{Float64}, f_ticks::Function, f_time::Function)
```

2つの集約LOB測定のベクトルを比較します。

`X`と`Y`の各列は異なる時点を示し、各行は異なるエントリ（おそらく異なるレベル）です。
