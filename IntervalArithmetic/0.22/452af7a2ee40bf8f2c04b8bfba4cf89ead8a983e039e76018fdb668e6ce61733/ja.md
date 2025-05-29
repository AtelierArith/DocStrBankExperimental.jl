```
Constant(value)
```

区間演算に対応した定数関数です。

区間入力の場合は値のみを含む区間を返し、それ以外の場合は値を直接返します。

```jldoctest
julia> c = Constant(1.2)
Constant{Float64}(1.2)

julia> c(22.2)
1.2

julia> c(interval(0, 1.3))
Interval{Float64}(1.2, 1.2, com)
```

これは、常に `value` を出力する base の `Returns(value)` とは異なることに注意してください。これは計算における区間の伝播を短絡させ、関連する正確性の保証を失う可能性があります。
