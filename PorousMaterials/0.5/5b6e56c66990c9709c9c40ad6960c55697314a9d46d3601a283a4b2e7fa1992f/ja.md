```
random_reinsertion!(molecule, box)
```

分子を移動および回転（必要に応じて）させ、元のコピーを保持して復元できるようにします。

# 引数

  * `molecule::Molecule{Frac}`: 移動および回転（必要に応じて）させる分子
  * `box::Box`: 回転に使用されるボックス

# 戻り値

  * `old_molecule::Molecule{Frac}`: 元の分子のコピー
