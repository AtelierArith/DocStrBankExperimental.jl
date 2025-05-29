```
QuadLimbDark(u::AbstractVector)
```

[`PolynomialLimbDark`](@ref) の最大2項（2次形式）を持つ専門的な実装です。これは数値積分なしで完全に閉じた形式の解を持っています。つまり、中間的な割り当てがなく、数値誤差が減少します。

# 数学的形式

$$
I(\mu) \propto 1 - u_1(1-\mu) - u_2(1-\mu)^2
$$

!!! warning "高次項"
    高次項は*無視されます*; エラーは発生しません


# 例

```jldoctest quad
ld = QuadLimbDark(Float64[]) # 定数項のみ

b = [0, 1, 2] # 影響パラメータ
r = 0.01 # 半径比
ld.(b, r)

# 出力
3-element Vector{Float64}:
 0.9999
 0.9999501061035608
 1.0
```

```jldoctest quad
ld = QuadLimbDark([0.4, 0.26]) # 最大2項
ld.(b, r)

# 出力
3-element Vector{Float64}:
 0.9998785437247428
 0.999974726693709
 1.0
```

# 参考文献

[`PolynomialLimbDark`](@ref) の参考文献を参照してください
