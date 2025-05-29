```
ELFDynEntries(oh::ELFHandle, kinds::Vector)
```

ELFオブジェクトからすべての`ELFDynEntry`オブジェクトを読み取り、渡された`kinds`のいずれかである場合は配列として返します。例えば、`DT_NEEDED`などです。
