```
uv(spec::Spectrum, chs::AbstractRange{<:Integer}=eachindex(spec))::Vector{UncertainValue}
```

スペクトル内のカウントデータを Vector{UncertainValue} に変換します。カウント統計は C ± √C で近似できると仮定します。
