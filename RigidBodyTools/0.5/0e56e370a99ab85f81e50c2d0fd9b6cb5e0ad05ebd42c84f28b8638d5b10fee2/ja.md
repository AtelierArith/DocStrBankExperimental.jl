```
rebase_from_inertial_to_reference(Xi_to_A::MotionTransform,x::AbstractVector,m::RigidBodyMotion,reference_body::Int)
```

`Xi_to_A`が慣性座標から他の座標A（例えば、ある物体の座標）への運動変換を表す場合、この関数は参照物体の座標から座標Aへの運動変換を返します。これは、現在のジョイント状態ベクトル`x`を使用して、システム`m`の変換リストを構築します。
