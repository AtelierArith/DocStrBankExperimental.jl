```
MPITopology{N}
```

N次元のCartesian MPI分解トポロジーを説明します。

---

```
MPITopology(comm::MPI.Comm, pdims::Dims{N})
```

N次元のMPIトポロジー情報を作成します。

`pdims`タプルは、トポロジーの各次元に配置するMPIプロセスの数を指定します。その値の積は、コミュニケーター`comm`のプロセス数と等しくなければなりません。

# 例

2Dトポロジーを4×2ブロックに分割します：

```julia
comm = MPI.COMM_WORLD
@assert MPI.Comm_size(comm) == 8
topology = MPITopology(comm, (4, 2))
```

---

```
MPITopology(comm::MPI.Comm, Val(N))
```

コミュニケーター内のすべてのMPIプロセス間でデータのN次元分解を定義する便利な`MPITopology`コンストラクタです。

各N次元に沿った分割数は、[`MPI.Dims_create`](https://juliaparallel.org/MPI.jl/stable/reference/topology/#MPI.Dims_create)の呼び出しによって自動的に決定されます。

# 例

2D分解グリッドを作成します：

```julia
comm = MPI.COMM_WORLD
topology = MPITopology(comm, Val(2))
```

---

```
MPITopology{N}(comm_cart::MPI.Comm)
```

Cartesianトポロジーを持つMPIコミュニケーターからトポロジー情報を作成します（通常は[`MPI.Cart_create`](https://juliaparallel.org/MPI.jl/stable/reference/topology/#MPI.Cart_create)を使用して構築されます）。トポロジーは次元`N`を持たなければなりません。

# 例

2Dトポロジーを4×2ブロックに分割します：

```julia
comm = MPI.COMM_WORLD
@assert MPI.Comm_size(comm) == 8
pdims = (4, 2)
comm_cart = MPI.Cart_create(comm, pdims)
topology = MPITopology{2}(comm_cart)
```
