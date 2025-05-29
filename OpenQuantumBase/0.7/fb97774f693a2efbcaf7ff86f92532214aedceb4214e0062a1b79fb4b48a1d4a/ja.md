```
function ConstantCouplings(c::Vector{T}; sp = false, unit=:h) where T <: AbstractString
```

最初の引数が文字列の1次元配列である場合、コンストラクタは文字列表現によって表される行列を自動的に構築します。
