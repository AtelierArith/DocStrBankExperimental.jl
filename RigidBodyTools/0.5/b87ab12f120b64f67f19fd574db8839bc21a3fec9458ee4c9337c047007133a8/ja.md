```
update_body!(b::Body,T::MotionTransform)
```

与えられた `MotionTransform` を使用して、ボディを（インプレースで）変換します。この変換 `T`（システムAからシステムBへの変換を定義する）を使用する際、Aは慣性座標系として解釈され、Bはボディシステムとして解釈されます。したがって、`T` の位置ベクトルは、慣性座標におけるボディの相対位置として解釈され、回転演算子の逆が適用されてボディ固定座標を慣性フレームに変換します。
