```
expected_loglikelihood(::DefaultExpectationMethod, lik, q_f::AbstractVector{<:Normal}, y::AbstractVector)
```

与えられた尤度に対して、デフォルトの数値積分法を使用した期待対数尤度。(デフォルトの数値積分法は `default_expectation_method(lik)` によって定義され、存在する場合は閉じた形の解であるべきですが、そうでない場合はガウス-エルミート数値積分にデフォルトします。)
