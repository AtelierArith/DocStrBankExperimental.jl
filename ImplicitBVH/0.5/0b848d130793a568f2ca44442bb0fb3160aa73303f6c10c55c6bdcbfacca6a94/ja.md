```julia
struct BVHOptions{I<:Integer, T}
```

バウンディングボリューム階層を構築およびトラバースするためのオプションで、並列戦略設定を含みます。

インデックスの例（例：`Int32(0)`）が使用され、BVH構築（[`ImplicitTree`](@ref)、order）およびトラバース（[`IndexPair`](@ref））に使用されるインデックスの型を推測します。

CPUスケジューラは、`:threads`（基本的なJuliaスレッド用）または`:polyester`（Polyester.jlスレッド用）に設定できます。

`compute_extrema=false`で`mins` / `maxs`が定義されている場合、バウンディングボリュームの分布から計算されません。たとえば、固定されたシミュレーションボックスがある場合に便利です。これらの境界にバウンディングボリュームの中心が触れたり、外側に出たりしないことを**必ず**確認してください。そうしないと、論理的に不正確な結果が静かに生成されます。

# メソッド

```
BVHOptions(;

    # 型を推測するための例のインデックス
    index_exemplar::I               = Int32(0),

    # CPUスレッド
    scheduler::Symbol               = :threads,
    num_threads::Int                = Threads.nthreads(),
    min_mortons_per_thread::Int     = 1000,
    min_boundings_per_thread::Int   = 1000,
    min_traversals_per_thread::Int  = 1000,

    # GPUスケジューリング
    block_size::Int                 = 256,

    # 最小値 / 最大値
    compute_extrema::Bool           = true,
    mins::NTuple{3, T}              = (NaN32, NaN32, NaN32),
    maxs::NTuple{3, T}              = (NaN32, NaN32, NaN32),
) where {I <: Integer, T}
```

# フィールド

  * `index_exemplar::Integer`
  * `scheduler::Symbol`
  * `num_threads::Int64`
  * `min_mortons_per_thread::Int64`
  * `min_boundings_per_thread::Int64`
  * `min_traversals_per_thread::Int64`
  * `block_size::Int64`
  * `compute_extrema::Bool`
  * `mins::Tuple{T, T, T} where T`
  * `maxs::Tuple{T, T, T} where T`
