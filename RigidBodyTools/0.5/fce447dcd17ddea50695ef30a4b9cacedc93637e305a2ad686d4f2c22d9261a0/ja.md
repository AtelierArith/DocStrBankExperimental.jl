```
child_joints_of_body(bodyid,ls::RigidBodyMotion)
```

システム `ls` におけるボディ `bodyid` の子関節のインデックス（存在する場合）を返します。この関数は `bodyid = 0` も受け付け、慣性座標系に接続されているボディの関節のインデックスを返します。
