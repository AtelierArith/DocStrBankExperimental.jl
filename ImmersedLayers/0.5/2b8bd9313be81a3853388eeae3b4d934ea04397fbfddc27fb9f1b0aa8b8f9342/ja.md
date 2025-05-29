```
laplacian!(w::GridData,s::GridData,cache::BasicILMCache)
```

グリッドデータ`s`のラプラシアンを計算し、`cache`が`IndexScaling`を持つ場合は1で、`GridScaling`を持つ場合はグリッドセルサイズで結果を割り、結果を`w`として返します。
