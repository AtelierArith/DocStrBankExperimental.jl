```
addconstraint!(P::AbstractPolyhedron, constraint::HalfSpace)
```

制約表現での集合に線形制約をインプレースで追加します。

### 入力

  * `P`          – 制約表現での集合
  * `constraint` – 追加する線形制約

### 注意事項

すべての線形制約の次元が同じであることをユーザーが保証する必要があります。
