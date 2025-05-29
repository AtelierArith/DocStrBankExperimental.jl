```
rotate!(scene::Transformable, axis_rot::Quaternion)
rotate!(scene::Transformable, axis_rot::AbstractFloat)
rotate!(scene::Transformable, axis_rot...)
```

シーンに絶対回転を適用します。回転はすべて内部的に`Quaternion`に変換されます。
