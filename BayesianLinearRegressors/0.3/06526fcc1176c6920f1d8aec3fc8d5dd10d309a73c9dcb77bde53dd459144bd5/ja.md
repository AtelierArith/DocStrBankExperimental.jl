```
BasisFunctionRegressor{Tblr,Tϕ}
```

Basis Function Regressorは、入力`x`がまず基底関数ϕを通じて特徴空間にマッピングされるベイズ線形回帰器を表します。

ϕは、ベイズ線形回帰器に対して許可されている入力タイプのいずれか（ColVecs、RowVecs、またはMatrix{<:Real} - 詳細はパッケージのREADMEを参照）を受け入れ、これらの許可されたタイプのいずれかを出力する関数でなければなりません。

```jldoctest; output = false
x = RowVecs(hcat(range(-1.0, 1.0, length=5)))
blr = BayesianLinearRegressor(zeros(2), Diagonal(ones(2)))

ϕ(x::RowVecs) = RowVecs(hcat(ones(length(x)), prod.(x)))
bfr = BasisFunctionRegressor(blr, ϕ)

var(bfr(x))

# output

5-element Vector{Float64}:
 2.0
 1.25
 1.0
 1.25
 2.0
```

基底関数回帰の詳細については、[1]、セクション3.1を参照してください。

[1] - C. M. Bishop. "Pattern Recognition and Machine Learning". Springer, 2006.
