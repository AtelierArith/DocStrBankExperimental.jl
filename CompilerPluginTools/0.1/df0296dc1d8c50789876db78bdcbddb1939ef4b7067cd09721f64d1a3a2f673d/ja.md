```
inline_const!(ir::IRCode)
```

これは `IRCode` に対して定数伝播を行いますので、抽象解釈中の定数伝播の後に、`IRCode` 内の定数値を強制的にインライン化することができます。
