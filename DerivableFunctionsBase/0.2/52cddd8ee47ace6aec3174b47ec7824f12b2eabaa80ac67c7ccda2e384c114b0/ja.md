```
DerivableFunction(F::Function; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, testinput::Union{Number,AbstractVector{<:Number}}; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, dF::Function; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, dF::Function, ddF::Function)
```

与えられた関数の導関数（および入力-出力の次元）を保存し、導関数が既知の場合に計算を高速化する可能性があります。
