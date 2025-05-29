```
DiagonalizingOrthonormalBasis{𝔽,TV} <: AbstractOrthonormalBasis{𝔽,TangentSpaceType}
```

接地空間の接ベクトルのベクトルとしての直交正規基底 `Ξ`（長さは [`manifold_dimension`](@ref) によって決定される）で、曲率テンソル $R(u,v)w$ を対角化し、方向 `frame_direction` $v$ の曲率が `0` である。

型パラメータ `𝔽` は、基底ベクトルの線形結合において係数として使用される [`AbstractNumbers`](@ref) を示す。

# コンストラクタ

```
DiagonalizingOrthonormalBasis(frame_direction, 𝔽::AbstractNumbers = ℝ)
```
