```
GaussFunc{T, F1, F2} <: AbstractGaussFunc{T}
```

収束した原始ガウス型関数。

≡≡≡ フィールド ≡≡≡

`xpn::ParamBox{T, :α, F1}`：指数係数。

`con::ParamBox{T, :d, F2}`: 縮約係数。

`param::Tuple{ParamBox{T, α}, ParamBox{T, d}}`: `GaussFunc` 内のパラメータコンテナ。

≡≡≡ 初期化メソッド ≡≡≡

```
GaussFunc(e::Union{T, Array{T, 0}, ParamBox{T}}, d::Union{T, ParamBox{T}}) where 
         {T<:AbstractFloat} -> 
GaussFunc{T}
```
