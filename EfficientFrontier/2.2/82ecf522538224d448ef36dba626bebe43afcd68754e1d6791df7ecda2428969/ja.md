```
    Settings(P::Problem; kwargs...)        指定された問題に対するデフォルト設定
    Settings(; kwargs...)       デフォルト設定はFloat64型によって設定されます
    Settings{T<:AbstractFloat}(; kwargs...)
```

kwargsはFloat64およびBigFloatのためのSettings{T<:AbstractFloat}のフィールドからのものです

```
        tol::T         #2^-26 ≈ 1.5e-8  一般的なスカラー
        tolN::T        #2^-26 ≈ 1.5e-8  ノルム用
        tolS::T        #2^-26 ≈ 1.5e-8  Sを特定するため
        tolL::T        #2^-26 ≈ 1.5e-8  L用
        tolG::T        #2^-27 ≈ 7.5e-9  ギリシャ文字（ベータおよびガンマ）用
        muShft::T      #2^-18 ≈ 3.8e-6  muを(1 +/- muShft)*muにシフト
```
