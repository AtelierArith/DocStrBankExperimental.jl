```
body_velocities(x::AbstractVector,t::Real,ls::RigidBodyMotion) -> PluckerMotionList
```

剛体システム `ls` のための物体の速度を計算し、それぞれを独自の座標系で表現します。これを実行するために、関数は時刻 `t` における指定された運動学を持つ自由度の速度を評価し、状態ベクトル `x` から残りの自由な自由度（外因性および制約のないもの）を取得します。
