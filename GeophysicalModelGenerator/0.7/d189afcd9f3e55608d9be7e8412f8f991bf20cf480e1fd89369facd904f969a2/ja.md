```
fe_swap = swap_yz_dims(fe_data::FEData)
```

これはFEDataオブジェクトの`y`と`z`の次元を入れ替えます。これはpTatinにとって便利で、pTatinでは`y`がGMGの`z`に相当します。
