```
rxxlayer!(circuit, topology)
```

トポロジー内の各ペアに対して、回路に二量子ビット `PauliRotation([:X, :X], pair)` ゲートの層を追加します。
