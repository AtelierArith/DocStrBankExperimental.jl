```
rzzlayer!(circuit, topology)
```

トポロジー内の各ペアに対して、回路に二量子ビット `PauliRotation([:Z, :Z], pair)` ゲートの層を追加します。
