```
@parallel_indices indices kernel
@parallel_indices indices inbounds=... memopt=... ndims=... kernel
```

`kernel` を並列に宣言し、[`@init_parallel_stencil`](@ref) で選択した並列化パッケージを使用して `kernel` 内で指定された並列 `indices` を生成します。

# オプションのキーワード引数

```
- `inbounds::Bool`: カーネルに `@inbounds` を適用するかどうか。デフォルトは `false` で、[`@init_parallel_stencil`](@ref) の `inbounds` キーワード引数で設定された値です。
- `memopt::Bool=false`: 高度なステンシル特有のオンチップメモリ最適化を実行するかどうか。`memopt=true` が設定されている場合、対応するカーネル呼び出しでも設定する必要があります。
!!! note "高度なオプションのキーワード引数"
    - `ndims::Integer|Tuple`: `indices` に対してスプラット構文を使用する際に必要なインデックス次元の数：1、2、3（デフォルトの `ndims` 値は [`@init_parallel_stencil`](@ref) の対応するキーワード引数で設定できます）または、与えられた `ndims` 値ごとにメソッドを生成するための前述のいずれかを含むタプル。具体的には、スプラット構文（例：`@parallel_indices (I...) ndims=(2,3) ...`）は、`ndims` 値によって長さが与えられる並列インデックスのタプル（この例では `I`）を生成します（ここでは最初のメソッドに対して `2`、2 番目のメソッドに対して `3`）。これにより、次元数に依存しないカーネルを書くことが可能になります（例えば、配列 `A` の要素にアクセスするために `A[I...]` と書くことができます）。キーワード引数 `N` は、次元数に基づいてディスパッチするために `ndims` がタプルである場合に必須になります（以下を参照）。
    - `N::Integer|Tuple`: カーネルメソッドシグネチャ内の型パラメータ `N` が取るべき値。値は通常、`@parallel_indices` マクロまたは `@init_parallel_stencil` の対応するキーワード引数で設定された `ndims` に基づいて計算され、評価前に式に置き換えられます。これにより、カーネルメソッド内で次元数に基づいてディスパッチすることが可能になります（例：`@parallel_indices (I...) ndims=(1,3) N=ndims function f(A::Data.Array{N}) ... end`）。キーワード引数 `N` は、`ndims` がタプルである場合に必須であり、その場合は `ndims` と同じ長さのタプルでなければなりません。
```

参照： [`@init_parallel_stencil`](@ref)
