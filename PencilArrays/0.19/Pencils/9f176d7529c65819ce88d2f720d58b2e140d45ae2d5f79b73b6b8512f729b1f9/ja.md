```
Pencil{N,M}
```

は、`N`次元配列を`M`方向（`M < N`）に沿ってMPIプロセス間で分解することを説明します。

---

```
Pencil(
    [A = Array],
    topology::MPITopology{M}, size_global::Dims{N},
    decomp_dims::Dims{M} = default_decomposition(N, Val(M));
    permute::AbstractPermutation = NoPermutation(),
    timer = TimerOutput(),
)
```

`N`次元の幾何学を`M`次元に沿って分解します。

幾何学の次元は`size_global = (N1, N2, ...)`によって与えられます。`Pencil`は、MPIプロセスのグループ間で次元`size_global`の配列の分解を説明します。

データは、与えられた`M`次元のMPIトポロジーに分配されます（`M ≤ N`）。

分解された次元は、`decomp_dims`引数を介してオプションで提供できます。デフォルトでは、`M`の右端の次元が分解されます。たとえば、5Dデータの2D分解（`M = 2`および`N = 5`）の場合、次元`(4, 5)`がデフォルトで分解されます。

すべての次元に分配することも可能です（`M = N`）。この特定のケースでは、[転置](@ref Global-MPI-operations)は現在不可能であることに注意してください。

オプションの引数`A`は、基本の`Array`型以外の配列で作業することを可能にします。特に、`CuArray`のようなGPU配列型で作業する際に便利です。

オプションの`permute`パラメータは、データインデックスの**論理順序**（コード内で配列にアクセスする順序）から**メモリ順序**（メモリ内のインデックスの実際の順序）への置換を示すために使用できます。置換は、`permute = Permutation(3, 1, 2)`のようにエクスポートされた`Permutation`型を使用して指定する必要があります。

コンストラクタに`TimerOutput`を渡すことも可能です。詳細については、[パフォーマンスの測定](@ref PencilArrays.measuring_performance)を参照してください。

# 例

グローバル次元$N_x × N_y × N_z = 4×8×12$の3D幾何学を2番目（$y$）および3番目（$z$）の次元に沿って分解します：

```jldoctest
julia> topo = MPITopology(MPI.COMM_WORLD, Val(2));

julia> Pencil(topo, (4, 8, 12), (2, 3))
3Dデータの分解
    データ次元: (4, 8, 12)
    分解された次元: (2, 3)
    データ置換: NoPermutation()
    配列型: Array

julia> Pencil(topo, (4, 8, 12), (2, 3); permute = Permutation(3, 2, 1))
3Dデータの分解
    データ次元: (4, 8, 12)
    分解された次元: (2, 3)
    データ置換: Permutation(3, 2, 1)
    配列型: Array

```

2番目のケースでは、実際のデータは各MPIプロセス内で`(z, y, x)`順序で格納されます。

---

```
Pencil([A = Array], size_global::Dims{N}, [decomp_dims = (2, …, N)], comm::MPI.Comm; kws...)
```

暗黙的に[`MPITopology`](@ref)を作成する便利なコンストラクタです。

`decomp_dims`で指定された分解された次元の数は`M < N`でなければなりません。`decomp_dims`が渡されない場合、次元`2:N`が分解されます。

キーワード引数は、`MPITopology`を受け取る別のコンストラクタに渡されます。より多くの制御が必要な場合は、そのコンストラクタを使用する必要があります。

# 例

```jldoctest
julia> Pencil((4, 8, 12), MPI.COMM_WORLD)
3Dデータの分解
    データ次元: (4, 8, 12)
    分解された次元: (2, 3)
    データ置換: NoPermutation()
    配列型: Array

julia> Pencil((4, 8, 12), (1, ), MPI.COMM_WORLD)
3Dデータの分解
    データ次元: (4, 8, 12)
    分解された次元: (1,)
    データ置換: NoPermutation()
    配列型: Array
```

---

```
Pencil(
    [A = Array],
    p::Pencil{N,M};
    decomp_dims::Dims{M} = decomposition(p),
    size_global::Dims{N} = size_global(p),
    permute::P = permutation(p),
    timer::TimerOutput = timer(p),
)
```

既存のものから新しいペンシル構成を作成します。

このコンストラクタは、2つのペンシル構成間で一時データバッファを共有することを可能にし、グローバルメモリ使用量を削減します。
