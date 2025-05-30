```
Joint(jtype::AbstractJointType,parent_id,Xp_to_j::MotionTransform,child_id,Xch_to_j::MotionTransform,
        dofs::Vector{AbstractDOFKinematics};[params=Dict()])
```

`jtype`のタイプのジョイントを構築し、`parent_id`の親ボディを`child_id`の子ボディに接続します。ジョイントのボディ上の配置は、親および子の座標系からジョイントシステムへの変換である`Xp_to_j`および`Xch_to_j`によって示されます。ジョイントの自由度は、`dofs`という`AbstractDOFKinematics`のベクターで指定されます。ジョイントに必要なパラメータは、オプションの`params`辞書で渡すことができます。
