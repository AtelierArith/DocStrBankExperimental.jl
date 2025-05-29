```
@trues(args...)
@trues(args..., <キーワード引数>)
```

`trues(args...)`を呼び出します。ここで、関数`trues`は、[`@init_parallel_stencil`](@ref)で選択された並列化用のパッケージと互換性があるように選ばれます。

# キーワード引数

  * `celldims::Integer|NTuple{N,Integer}=1`: 各配列セルの次元。各セルは単一の値（デフォルト）または指定された次元のN次元配列を含むことができます。

!!! note "高度な情報"
      * `blocklength::Integer`: 同じ`Cell`フィールドの値の量が連続して格納されることを指します（`blocklength=1`は構造体のような配列ストレージを意味します; `blocklength=prod(dims)`は配列のようなストレージの配列構造体を意味します; `blocklength=0`は`blocklength=prod(dims)`のエイリアスで、より専門的なディスパッチのおかげでパフォーマンスが向上します）。デフォルトでは、`blocklength`は、[`@init_parallel_stencil`](@ref)でGPUパッケージが選択された場合は自動的に`0`に設定され、CPUパッケージが選択された場合は`1`に設定されます。さらに、引数`blocklength`は、`celldims`または`celltype`のいずれかが設定されている場合にのみ効果があります。それ以外の場合は無視されます。


関連情報: [`@zeros`](@ref), [`@ones`](@ref), [`@rand`](@ref), [`@falses`](@ref), [`@fill`](@ref), [`@CellType`](@ref) ```
