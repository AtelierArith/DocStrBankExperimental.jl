```
update_param!(mi::ModelInstance, name::Symbol, value)
```

`ModelInstance` `mi`のモデルパラメータの`value`を、`name`で参照して更新します。これはモデルを汚さないため、UNSAFEな更新であり、私たちのMCS作業のような特定の目的のために注意して使用する必要があります。
