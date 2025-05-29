```
scale!([mode = Absolute], t::Transformable, xyz...)
scale!([mode = Absolute], t::Transformable, xyz::VecTypes)
```

与えられた `t::Transformable`（シーンまたはプロット）を、指定された引数 `xyz` にスケールします。欠けている次元は1でスケールされます。`mode == Accum` の場合、指定されたスケーリングは前のものと掛け合わされます。
