```
allocate(::Backend, Type, dims...)::AbstractArray
```

計算バックエンドに適したストレージ配列を割り当てます。

!!! note
    バックエンドの実装は**必ず** `allocate(::NewBackend, T, dims::Tuple)`を実装しなければなりません。

