```
kvectors = precompute_kvec_wts(kreps, box, α, max_mag_k_sqrd=Inf)
```

速度のために、フーリエ空間におけるエヴァルド和の各逆格子ベクトルの重みを事前に計算します。この関数は対称性を利用しています：cos(-k⋅(x-xᵢ)) + cos(k⋅(x-xᵢ)) = 2 cos(k⋅(x-xᵢ))

`max_mag_k_sqrd`が渡されると、`max_mag_k_sqrd`より大きい大きさのkベクトルは含まれません。

# 引数

  * `kreps::Tuple{Int, Int, Int}`: a, b, cに必要なkベクトルの複製数
  * `box::Box`: 逆格子を含むシミュレーションボックス。
  * `α::Float64`: エヴァルド和の収束パラメータ（単位：逆Å）
  * `max_mag_k_sqrd::Float64`: フーリエ和における|k|²のカットオフ；渡された場合、この値より大きい大きさのkベクトルは含めない。

# 戻り値

  * `kvectors::Array{Kvector, 1}`: フーリエ和に含めるkベクトルの配列と、フーリエ和への寄与を示す対応する重み。
