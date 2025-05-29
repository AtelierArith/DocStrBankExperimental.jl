```
AbstractHMM{F<:VariateForm}
```

カスタムHMMタイプは、少なくとも次のインターフェースを実装する必要があります：

```julia
struct CustomHMM{F,T} <: AbstractHMM{F}
    a::AbstractVector{T}               # 初期状態分布
    A::AbstractMatrix{T}               # 遷移行列
    B::AbstractVector{Distribution{F}} # 観測分布
    # オプションのカスタムフィールド ....
end
```
