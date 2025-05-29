```
rm_compute(weight::Function,lb::Real,ub::Real,Npoly::Int=4,Nquad::Int=10;quadrature::Function=clenshaw_curtis)
```

正の `weight` 関数がドメイン `(lb,ub)` を持つ場合、すなわち関数 $w: [lb, ub ] \rightarrow \mathbb{R}_{\geq 0}$ であるとき、この関数は `Npoly` の再帰係数 `(α,β)` を生成します。

キーワード `quadrature` は、使用される数値積分法を指定します。
