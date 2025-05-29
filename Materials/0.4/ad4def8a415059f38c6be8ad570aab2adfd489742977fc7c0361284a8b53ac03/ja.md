```
reset_material!(material::AbstractMaterial)
```

`material`内で、`ddrivers`、`dparameters`、および`variables_new`をゼロにします。これは、タイムステップが計算されたが、まだ確定されていない仮の状態をクリアします。

`update_material!`によって内部的に使用されます。
