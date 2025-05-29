```
Transition <: QSym
Transition(h::NLevelSpace,name::Symbol,i,j)
```

レベル `j` からレベル `i` への遷移を定義する基本演算子です [`NLevelSpace`](@ref) 上で。記法はディラック記法に対応しており、上記は `|i⟩⟨j|` と同等です。

# 例

```
julia> ha = NLevelSpace(:a,(:g,:e))
ℋ(a)

julia> σ = Transition(ha,:σ,:g,:e)
σge
```
