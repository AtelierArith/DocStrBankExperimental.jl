```
@zeros(args...)
@zeros(args..., <キーワード引数>)
```

`zeros(eltype, args...)`を呼び出します。ここで、`eltype`はデフォルトで[`@init_parallel_stencil`](@ref)で選択された`numbertype`であり、関数`zeros`は[`@init_parallel_stencil`](@ref)で選択された並列化用のパッケージと互換性があるように選ばれます（Threads用のzeros、CUDA用のCUDA.zeros、AMDGPU用のAMDGPU.zeros、Metal用のMetal.zeros）。

!!! note "高度な情報"
    `eltype`はキーワード引数として明示的に渡すことができ、[`@init_parallel_stencil`](@ref)で選択されたデフォルトの`numbertype`の代わりに使用されます。デフォルトの`numbertype`が[`@init_parallel_stencil`](@ref)で選択されていない場合、キーワード引数`eltype`は必須です。これは、パフォーマンスが重要な計算でデータ型の変換が発生しないように注意して使用する必要があります。


# キーワード引数

  * `eltype::DataType`: 要素の型（数値またはインデックス）。
  * `celldims::Integer|NTuple{N,Integer}=1`: 各配列セルの次元。各セルは単一の値（デフォルト）または指定された次元のN次元配列を含むことができます。

!!! note "高度な情報"
      * `celltype::DataType`: 各配列セルの型; マクロ`@CellType`で生成する必要があります。キーワード引数`celltype`は他のキーワード引数と互換性がありません: いずれかが設定されている場合、`celltype`は自動的に定義されます。`celltype`は名前付きセルフィールドを使用するためにのみ指定する必要があります。値は常に配列インデックスでアドレス指定できることに注意してください。たとえセルフィールド名が定義されていてもです。
      * `blocklength::Integer`: 同じ`Cell`フィールドの値が連続して格納される量を指します（`blocklength=1`は構造体のような配列ストレージを意味します; `blocklength=prod(dims)`は配列のようなストレージの配列構造体を意味します; `blocklength=0`は`blocklength=prod(dims)`のエイリアスで、より専門的なディスパッチのおかげでパフォーマンスが向上します）。デフォルトでは、`blocklength`は[`@init_parallel_stencil`](@ref)でGPUパッケージが選択された場合は自動的に`0`に設定され、CPUパッケージが選択された場合は`1`に設定されます。さらに、引数`blocklength`は`celldims`または`celltype`のいずれかが設定されている場合にのみ効果があります。それ以外の場合は無視されます。


参照: [`@ones`](@ref), [`@rand`](@ref), [`@falses`](@ref), [`@trues`](@ref), [`@fill`](@ref), [`@CellType`](@ref) ```
