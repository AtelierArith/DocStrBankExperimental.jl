```
addconstraint!(P::HPoly, constraint::HalfSpace)
```

制約表現における多面体に線形制約を追加します。

### 入力

  * `P`          – 制約表現における多面体
  * `constraint` – 追加する線形制約

### 注意事項

すべての線形制約の次元が同じであることをユーザーが保証する必要があります。
