```
⊗(spaces::HilbertSpace...)
```

複数の部分空間からなる [`ProductSpace`](@ref) を作成します。Unicode `\otimes<tab>` は [`tensor`](@ref) のエイリアスです。

# 例

```
julia> hf = FockSpace(:f)
ℋ(f)

julia> ha = NLevelSpace(:a,2)
ℋ(a)

julia> h = hf⊗ha
ℋ(f) ⊗ ℋ(a)
```
