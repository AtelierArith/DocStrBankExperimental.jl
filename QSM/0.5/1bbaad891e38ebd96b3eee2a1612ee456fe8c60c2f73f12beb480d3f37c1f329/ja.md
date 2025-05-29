```
dipole_kernel(sz, vsz; kwargs...) =
    dipole_kernel(Float64, sz, vsz; kwargs...)

dipole_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real};
    bdir::NTuple{3, Real} = (0, 0, 1),
    method::Symbol = :kspace,
    dsz::NTuple{3, Integer} = sz,
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

双極子カーネル。

デフォルトでは、双極子カーネルはk空間で構築され、インデックス `(1,1,1)` に中心を置きます。

### 引数

  * `sz::NTuple{3, Integer}`: 配列サイズ
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `method::Symbol = :kspace`: 画像空間 `(:i, :ispace)` または k空間 `(:k, :kspace)` で作成
  * `dsz::NTuple{3, Integer} = sz`:

      * `method ∈ (:k, :kspace)`: 未使用
      * `method ∈ (:i, :ispace)`: 画像空間での双極子カーネルサイズ
  * `transform::Union{Nothing, Symbol} = nothing`:

      * `method ∈ (:k, :kspace)`: `:rfft` または `:fft` k空間双極子カーネルを作成
      * `method ∈ (:i, :ispace)`: 画像空間双極子カーネルを変換 `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `method ∈ (:k, :kspace)`:   カーネルが `(1,1,1)` (`false`) または `N÷2+1` (`true`) に中心を置く
      * `method ∈ (:i, :ispace) and transform = nothing`:   カーネルが `N÷2+1` (`false`) または `(1,1,1)` (`true`) に中心を置く
      * `method ∈ (:i, :ispace) and transform ∈ (:rfft, :fft)`:   カーネルが `(1,1,1)` (`false`) または `N÷2+1` (`true`) に中心を置く

### 戻り値

  * `Array{T, 3}`: 双極子カーネル
