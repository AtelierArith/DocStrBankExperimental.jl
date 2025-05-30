```
RigidBodyMotion
```

剛体の接続性と運動を含む型で、慣性系およびおそらく互いに、ジョイントを介してリンクされています。基本コンストラクタは `RigidBodyMotion(joints::Vector{Joint},nbody::Int)` であり、`joints` は [`Joint`](@ref) 型のジョイントのベクターを含み、各ジョイントは親体と子体の接続を指定します。（親は慣性座標系である可能性があります。）
