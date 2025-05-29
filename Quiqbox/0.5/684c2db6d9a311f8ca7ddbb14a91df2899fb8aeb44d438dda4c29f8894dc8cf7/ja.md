```
BasisFunc{T, D, 𝑙, GN, PT} <: FloatingGTBasisFuncs{T, D, 𝑙, GN, PT, 1}
```

定義された座標に割り当てられた中心を持つ（浮動）ガウス型基底関数。

≡≡≡ フィールド ≡≡≡

`center::SpatialPoint{T, D, PT}`: `D`次元の中心。

`gauss::NTuple{GN, GaussFunc{T, <:Any}}`: 基底関数内のガウス関数。

`l::Tuple{LTuple{D, 𝑙}}`: 角運動量のカルテジアン表現。例えば、`Quiqbox.LTuple{3, 1}((1, 0, 0))`（X¹Y⁰Z⁰）は、すべての成分の合計が`𝑙=1`である特定の角運動量構成に対応します。

`normalizeGTO::Bool`: 各`GaussFunc`が計算で正規化されるかどうか。

`param::NTuple{D+GN*2, ParamBox}`： 基底関数に格納されたすべての調整可能なパラメータ。

≡≡≡ 初期化メソッド ≡≡≡

```
BasisFunc(cen::SpatialPoint{T, D, PT}, 
          gs::Tuple{AbstractGaussFunc{T}, Vararg{AbstractGaussFunc{T}, GN-1}}, 
          l::Union{Tuple{LTuple{D, 𝑙}}, LTuple{D, 𝑙}}, normalizeGTO::Bool) where 
         {T, D, PT, 𝑙, GN} -> 
BasisFunc{T, D, 𝑙, GN, PT}

BasisFunc(cen::SpatialPoint{T, D, PT}, gs::AbstractGaussFunc{T}, 
          l::Union{Tuple{LTuple{D, 𝑙}}, LTuple{D, 𝑙}}, normalizeGTO::Bool) where 
         {T, D, PT, 𝑙, GN} -> 
BasisFunc{T, D, 𝑙, 1, PT}
```
