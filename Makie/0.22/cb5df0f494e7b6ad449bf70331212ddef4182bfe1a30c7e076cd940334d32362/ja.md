```
rotate!(t::Transformable, axis_rot::Quaternion)
rotate!(t::Transformable, axis_rot::Real)
rotate!(t::Transformable, axis_rot...)
```

変換可能なオブジェクトに絶対回転を適用します。回転はすべて内部的に `Quaternion` に変換されます。
