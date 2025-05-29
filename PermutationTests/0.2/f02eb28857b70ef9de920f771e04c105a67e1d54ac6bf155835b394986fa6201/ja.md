```julia
function μ0(x::UniData; 
    mean::Realo=nothing) 
```

ゼロ平均で中心を取った `x` を返します。

`mean` が提供されている場合は、それを中心にします。`mean` は実数でなければなりません。
