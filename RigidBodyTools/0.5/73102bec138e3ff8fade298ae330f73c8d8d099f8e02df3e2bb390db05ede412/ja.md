```
is_system_in_relative_motion(lsid::Int,ls::RigidBodyMotion) -> Bool
```

ID `lsid` のリンクされたシステムが相対運動にある場合、つまり、慣性システムに接続されていない1つ以上のジョイントが関数 `ismoving(joint)` に対して `true` を返す場合は `true` を返します。
