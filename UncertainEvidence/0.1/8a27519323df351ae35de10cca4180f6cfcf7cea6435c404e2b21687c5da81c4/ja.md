```
BPA = Dict{T,S} where {T<:Any, S<:Real}
```

基本的な確率評価（BPA）は、ダンプスター・シェーファー理論（DST）の文脈での計算のための基礎的なデータ構造です。

`bpa`を使用して自動的に正規化されたBPAを作成します。そうでない場合は、正規化のために`redistribute!`を使用します。

参照: [`bpa`](@ref), [`redistribute!`](@ref).
