```
boostedsurf(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
            phi::Integer=3, dist_func::Any=(e1, e2, w) -> sum(w.*abs.(e1 .- e2), dims=2); 
            f_type::String="continuous")::Array{Float64,1}
```

特徴量の重みをBoostedSURFアルゴリズムを使用して計算します。

---

# 参考文献:

  * Gediminas Bertasius, Delaney Granizo-MacKenzie, Ryan J. Urba-

nowicz, and Jason H. Moore. ゲノム全体の遺伝分析のためのブーステッド空間的に均一なReliefFアルゴリズム. ハノーバー, NH 03755, USA,

2013. ダートマス大学.
