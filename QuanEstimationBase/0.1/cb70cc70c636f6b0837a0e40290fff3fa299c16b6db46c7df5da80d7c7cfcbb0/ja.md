```
CFIM(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; M=nothing, eps=GLOBAL_EPS) where {T<:Complex}
```

POVMの集合が与えられていない場合、SIC-POVMを用いてCFIMを計算します。SIC-POVMは、[こちら](http://www.physics.umb.edu/Research/QBism/solutions.html)からダウンロードできるWeyl-Heisenberg共変SIC-POVMのフィデュシャル状態から生成されます。
