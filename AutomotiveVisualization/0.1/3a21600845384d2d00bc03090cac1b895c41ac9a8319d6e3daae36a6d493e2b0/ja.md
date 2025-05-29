```
TargetFollowCamera <: Camera
```

ID `target_id`の車両を追跡するカメラ。デフォルトでは、ターゲット車両はxおよびy方向で追跡されます。いずれかの方向の追跡は、`x`または`y`キーを希望の値に設定することで無効にできます。

# コンストラクタ

`TargetFollowCamera(target_id; x=NaN, y=NaN, kwargs...)`
