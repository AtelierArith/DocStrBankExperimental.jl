```
transitionwavelength(ion, transition::Tuple, chamber::Chamber; ignore_manualshift=false)
```

戻り値 `transition` の波長を返します。これは、`ion` が `T` 内の位置に基づいて経験するゼーマンシフトを含みます。`ion` は、`chamber` 内の希望するイオンのインデックスを示す Ion または Int のいずれかです。
