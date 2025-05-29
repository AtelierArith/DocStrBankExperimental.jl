```
energy(I::Ion, sublevel; B=0, ignore_manualshift=false)
```

`I`の`sublevel`のエネルギーを返します。ゼーマンシフトは、磁場`B`の値を設定することで含めることができます。手動シフトは、`ignore_manualshift=true`を設定することで省略できます。
