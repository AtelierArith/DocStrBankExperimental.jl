```
update_material!(material::AbstractMaterial)
```

`integrate_material!`の結果をコミットします。

`material`には、`drivers`に`ddrivers`を追加し、`parameters`に`dparameters`を追加し、`variables`を`variables_new`で置き換えます。その後、自動的に`reset_material!`を呼び出します。
