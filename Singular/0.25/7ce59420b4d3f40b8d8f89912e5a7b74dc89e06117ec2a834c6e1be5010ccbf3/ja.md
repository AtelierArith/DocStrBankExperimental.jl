```
isequal(I1::sideal{S}, I2::sideal{S}) where S <: SPolyUnion
```

与えられたイデアルが同じ生成子を同じ順序で持っている場合は `true` を返します。異なる生成子を持つ代数的に等しい2つのイデアルは `false` を返すことに注意してください。
