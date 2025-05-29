```
ConfigJoint(njoint,joint_type,shape1,shape2,body1,joint_dof,qJ_init)
```

単一のジョイントの構成情報を設定します。ジョイントは、1から6までの1つまたは複数の自由度を許可します。

## フィールド

  * `njoint`: Int、このボディ-ジョイントシステムのジョイントの総数
  * `joint_type`: String、"revolute"、"prismatic"、"cylindrical"、"planar"、"spherical"、"free"、および "custom" を許可します。詳細な情報は `JointType` セクションに記載されています。
  * `shape1`: 6要素のVector{Float64}。このジョイントの親ボディ座標における位置を説明します。shape1が最初のジョイントで使用される場合、それはこの最初のジョイントの慣性系に対する向きを示します。これは [θx, θy, θz, x, y, z] で記述されます。
  * `shape2`: 6要素のVector{Float64}。このジョイントの子ボディ座標における位置を説明します。通常、隣接する2つのボディ間に距離のギャップや角度のギャップがない場合、shape2はzeros(Float64,6)です。
  * `body1`: このジョイントの親ボディID
  * `joint_dof`: Vector{Float64}。joint_dofのサイズは指定された自由度の数に依存し、タイプ `Dof` を参照します。
  * `qJ_init`: Vector{Float64}。これは、このジョイントの親ボディに対する初期角度/変位です。サイズは指定された自由度の数と同じである必要があります。
  * `vJ_init`: Vector{Float64}。これは、このジョイントのローカルフレームにおける初期角速度です。サイズは指定された自由度の数と同じである必要があります。
