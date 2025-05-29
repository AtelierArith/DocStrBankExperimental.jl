```
BasisSetRepresentation(
    hamiltonian::AbstractHamiltonian, addr=starting_address(hamiltonian);
    sizelim=10^7, cutoff, filter, max_depth, minimum_size, sort=false, kwargs...
)
BasisSetRepresentation(hamiltonian::AbstractHamiltonian, addresses::AbstractVector; kwargs...)
```

演算子 `hamiltonian` の基底集合表現を、`addr` から到達可能なすべてのアドレスで積極的に構築します。単一のアドレスの代わりに、`addresses` のベクターを渡すことができます。

`dimension(hamiltonian) > sizelim` の場合、メモリオーバーフローを防ぐために `ArgumentError` がスローされます。この動作を無効にするには、`sizelim = Inf` を設定します。

期待される計算された行列要素の数 `nnzs` と、各行列列における非ゼロのオフ対角行列要素の推定数 `col_hint` を提供することで、パフォーマンスを向上させることができます。

エネルギーカットオフを提供すると、`cutoff` より大きい対角要素を持つ列と行をスキップします。代わりに、任意の `filter` 関数を使用することもできます。引数として渡されたアドレスはフィルタリングされません。`addresses` によって張られた部分空間にトランケートされた行列を生成するには、`filter = Returns(false)` を使用します。

`max_depth` を提供すると、ハミルトニアンを介して `starting_address` に接続されているアドレスのみを訪問することで、行列と基底のサイズが制限されます。同様に、`minimum_size` を提供すると、基底が少なくとも `minimum_size` の長さに達した後に構築プロセスが停止します。

`sort` を `true` に設定すると、行列の行と列がソートされます。これは、列の順序が重要な場合、例えば行列を比較する際に便利です。追加のキーワード引数は `Base.sortperm` に渡されます。

!!! warning
    ```
    返される基底と行列の行および列の順序は任意であり、
    非決定的です。順序が重要な場合は `sort=true` を使用してください。
    ```


## フィールド

  * `sparse_matrix`: 基底 `basis` における `hamiltonian` を表すスパース行列
  * `basis`: アドレスのベクター
  * `hamiltonian`: ハミルトニアン `hamiltonian`

## 例

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> hamiltonian = HubbardReal1D(BoseFS(1,0,0));

julia> bsr = BasisSetRepresentation(hamiltonian)
BasisSetRepresentation(HubbardReal1D(fs"|1 0 0⟩"; u=1.0, t=1.0)) with dimension 3 and 6 stored entries:3×3 SparseArrays.SparseMatrixCSC{Float64, Int32} with 6 stored entries:
   ⋅   -1.0  -1.0
 -1.0    ⋅   -1.0
 -1.0  -1.0    ⋅

julia> BasisSetRepresentation(hamiltonian, bsr.basis[1:2]; filter = Returns(false)) # アドレスを渡してトランケート
BasisSetRepresentation(HubbardReal1D(fs"|1 0 0⟩"; u=1.0, t=1.0)) with dimension 2 and 2 stored entries:2×2 SparseArrays.SparseMatrixCSC{Float64, Int32} with 2 stored entries:
   ⋅   -1.0
 -1.0    ⋅

julia> using LinearAlgebra; round.(eigvals(Matrix(bsr)); digits = 4) # 固有値
3-element Vector{Float64}:
 -2.0
  1.0
  1.0

julia> ev = eigvecs(Matrix(bsr))[:,1]; ev = ev .* sign(ev[1]) # 基底状態の固有ベクトル
3-element Vector{Float64}:
 0.5773502691896257
 0.5773502691896255
 0.5773502691896257

julia> dv = DVec(zip(bsr.basis, ev)) # 基底状態を DVec として
DVec{BoseFS{1, 3, BitString{3, 1, UInt8}},Float64} with 3 entries, style = IsDeterministic{Float64}()
  fs"|0 0 1⟩" => 0.57735
  fs"|0 1 0⟩" => 0.57735
  fs"|1 0 0⟩" => 0.57735
```

[`dimension`](@ref)、[`sparse`](@ref)、[`Matrix`](@ref)、[`starting_address`](@ref) のメソッドがあります。

[`AbstractHamiltonian`](@ref) インターフェースの一部です。さらに [`build_basis`](@ref) も参照してください。
