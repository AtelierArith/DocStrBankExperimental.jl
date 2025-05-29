```
BodyAerodynamics(wings::Vector{T}; 
                 kite_body_origin=zeros(MVec3)) where T <: AbstractWing
```

空力計算のための[BodyAerodynamics](@ref)オブジェクトを構築します。

このコンストラクタは、パネルの初期化、座標変換、および空力特性の処理を行い、シミュレーションの準備が整った完全に初期化された構造体を返します。

# 引数

  * `wings::Vector{T}`: 分析する翼のベクトルで、TはAbstractWing型です。

# キーワード引数

  * `kite_body_origin=zeros(MVec3)`: CAD参照フレームにおける凧本体参照フレームの原点
  * `va=[15.0, 0.0, 0.0]`: 見かけの風ベクトル
  * `omega=zeros(3)`: 凧本体フレームにおける回転率（x, y, z）

# 戻り値

  * パネルと翼で初期化された[BodyAerodynamics](@ref)オブジェクト

# 例

```julia
wing = RamAirWing("body.obj", "foil.dat")
body_aero = BodyAerodynamics([wing], va=[15.0, 0.0, 0.0], omega=zeros(3))
```
