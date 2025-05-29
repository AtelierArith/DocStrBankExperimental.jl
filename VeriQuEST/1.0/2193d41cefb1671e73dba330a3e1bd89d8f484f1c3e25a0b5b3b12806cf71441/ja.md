```
get_angles(resource::MBQCResourceState, ::SecretAngles)
```

指定された `MBQCResourceState` から秘密の角度を返します。

# 引数

  * `resource`: 秘密の角度を抽出するための `MBQCResourceState`。

# 例

```julia
angles = get_angles(resource, SecretAngles()) # リソースの秘密の角度を返します
```
