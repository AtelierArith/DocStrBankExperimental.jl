```
surface_velocity!(u::AbstractVector,v::AbstractVector,bl::BodyList,x::AbstractVector,m::RigidBodyMotion,t::Real[;axes=0,frame=axes,motion_part=:full])
```

ボディ `bl` 上の点の表面速度成分 `u` と `v` を計算します。この関数は、時刻 `t` における指定された運動学を評価し、状態ベクトル `x` から非指定（外因性および制約のない）速度を抽出します。この関数の動作を変更できるキーワード引数が3つあります：`axes` は返される成分が慣性座標系（0、デフォルト）で表現されるか、別のボディの座標（ボディID）で表現されるかを決定します；`frame` は運動が別の基準ボディの速度に対して測定されるべきことを指定します（デフォルトは0）；`motion_part` は参照ボディの速度全体が使用されるか（`:full`、デフォルト）、角運動部分のみ（`:angular`）、または線形部分のみ（`:linear`）を決定します。
