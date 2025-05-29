```
reactant_device(;
    force::Bool=false, client=missing, device=missing, sharding=missing
) -> Union{ReactantDevice, CPUDevice}
```

機能する場合は `ReactantDevice` オブジェクトを返します。そうでない場合、`force` が `true` の場合はエラーをスローします。`force` が `false` の場合は `CPUDevice` にフォールバックします。

`client` と `device` は使用するクライアントと特定のデバイスを指定するために使用されます。指定されていない場合は、デフォルトのクライアントとインデックスが使用されます。

`sharding` はシャーディング戦略を指定するために使用されます。`Reactant.Sharding.AbstractSharding` が指定されている場合は、それを使用してすべての抽象配列をシャーディングします。あるいは、特定のリーフのシャーディングを指定するために `IdDict` を渡します。
