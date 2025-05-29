```
solveS(networks, connections; small_splitters::Bool = true,
    factorization = KLUfactorization(), internal_ports::Bool = false,
    nbatches::Integer = Base.Threads.nthreads())
```

`networks`で指定されたネットワーク間の接続を、タプルのベクトルのベクトル`connections`によって行います。外部ポート`S`の散乱パラメータのスパース行列と、外部ポート`ports`を返します。また、内部ポートの散乱パラメータ`Sinternal`と内部ポート`portsinternal`も返します。

# 引数

  * `networks`: ネットワーク名、散乱パラメータ行列、およびオプションでポートを含むタプルのベクトル。例としては、[("network1name",rand(Complex{Float64},2,2))] または [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])].
  * `connections::AbstractVector{<:AbstractVector{Tuple{T,Int}}}`: ネットワーク名とポートのタプルのベクトルのベクトル。例としては、[[("S1",1),("S2",2)]] または [[("network1name",1),("network2name",2)]] で、network1とnetwork2は接続される2つのネットワークであり、1と2は接続するポートを説明する整数です。

# キーワード

  * `small_splitters::Bool = true`: trueの場合、(N-2)の3ポートスプリッタを組み合わせてNポートスプリッタを生成します。falseの場合、Nポートスプリッタを作成し、コンポーネントをそれに接続します。
  * `factorization = KLUfactorization()`: デフォルトでKLU因子分解を使用します。JosephsonCircuits.LUfactorization()も良い選択肢です。キーワード引数は、これらの関数へのキーワード引数としてソルバーに渡すことができます。
  * `internal_ports::Bool = false`: 内部ポートの散乱パラメータを返します。
  * `nbatches::Integer = Base.Threads.nthreads()`: スレッドで実行するバッチの数。デフォルトは、Juliaが起動されたスレッドの数です。

# 返り値

  * `S`: 外部ポートの散乱パラメータのスパース行列。
  * `ports`: 外部ポートのネットワーク名とポート番号のタプルのベクトル。
  * `Sinternal`: 内部ポートの散乱パラメータのスパース行列。
  * `portsinternal`: 内部ポートのネットワーク名とポート番号のタプルのベクトル。

# 例

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])];
connections = [[("S1",1),("S2",2)]];
JosephsonCircuits.solveS(networks,connections;internal_ports=true)

# output
(S = [0.5 0.5; 0.5 0.5], ports = [("S1", 2), ("S2", 1)], Sinternal = [1.0 0.0; 0.5 0.5], portsinternal = [("S1", 1), ("S2", 2)])
```

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5],[("S3",5),("S3",6)])];
connections = [("S1","S3",1,6)];
JosephsonCircuits.solveS(networks,connections)

# output
(S = [0.5 0.5; 0.5 0.5], ports = [("S1", 2), ("S3", 5)], Sinternal = Float64[], portsinternal = [("S1", 1), ("S3", 6)])
```

# 参考文献

V. A. Monaco and P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.
