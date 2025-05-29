```
@qnumbers
```

演算子の構築のための便利なマクロ。

# 例

```
julia> h = FockSpace(:fock)
ℋ(fock)

julia> @qnumbers a::Destroy(h)
(a,)

julia> h = FockSpace(:one) ⊗ FockSpace(:two)
ℋ(one) ⊗ ℋ(two)

julia> @qnumbers b::Destroy(h,2)
(b,)
```
