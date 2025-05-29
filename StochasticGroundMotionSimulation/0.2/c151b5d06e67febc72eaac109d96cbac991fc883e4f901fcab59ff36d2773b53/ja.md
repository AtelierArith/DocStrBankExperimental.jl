```
fourier_source(f::T, m::S, src::SourceParameters) where {S<:Real,T<:Float64}
```

変位のソースフーリエ振幅スペクトル、定数項なし。これは単に地震モーメントとソーススペクトル形状を含みます。

参照: [`fourier_source_shape`](@ref)
