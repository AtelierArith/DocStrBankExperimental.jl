```julia
joint_transform(state, joint)
joint_transform(state, joint, safe)

```

与えられたジョイントのためのジョイント変換を返します。すなわち、`frame_after(joint)` から `frame_before(joint)` への変換です。
