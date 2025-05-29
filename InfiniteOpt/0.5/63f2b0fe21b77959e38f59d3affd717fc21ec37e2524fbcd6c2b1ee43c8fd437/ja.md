```
set_infinite_domain(pref::GeneralVariableRef, domain::InfiniteScalarDomain)::Nothing
```

無限パラメータ `pref` のスカラー無限ドメインを `domain` に指定します。これにより、基になるパラメータオブジェクトに含まれるすべてのサポートがリセット/削除されることに注意してください。また、`pref` が測定によって使用されている場合はエラーが発生します。`pref` が無限パラメータでない場合は `ArgumentError` がスローされます。
