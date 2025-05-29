```
struct Momentum{V,S,SS} <: AbstractMomentumModel
    U::V 
    p::S 
    sources::SS
end
```

重要な運動量フィールドを含む運動量モデル。

### フィールド

  * 'U'        – 速度ベクトルフィールド。
  * 'p'        – 圧力スカラー場。
  * 'sources'  – 運動量モデルのソース。

### 例

  * `Momentum(mesh::AbstractMesh)
