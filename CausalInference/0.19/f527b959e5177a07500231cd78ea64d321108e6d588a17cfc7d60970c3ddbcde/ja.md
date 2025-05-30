```
pcalg(t::T, p::Float64; cmitest::typeof(cmitest); kwargs...) where{T}
```

表形式の入力データ t に対して PC アルゴリズムを実行し、条件付き相互情報量の順列検定を使用して条件付き独立性を検出するために p 値 p を使用します。
