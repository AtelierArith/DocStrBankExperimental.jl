```
CFIM(ρ::Matrix{T}, dρ::Matrix{T}; eps=GLOBAL_EPS) where {T<:Complex}
```

単一パラメータのケースに適用し、POVMのセットが与えられていない場合。SIC-POVMを用いてCFIを計算します。
