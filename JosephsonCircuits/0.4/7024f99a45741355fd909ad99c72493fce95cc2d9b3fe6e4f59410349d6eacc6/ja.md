```
connectS(networks, connections; small_splitters::Bool = true,
    nbatches::Int = Base.Threads.nthreads())
```

`networks`内のネットワークを`connections`内の接続に従って接続した結果として、ネットワークとポートを返します。`networks`は、ネットワーク名と散乱パラメータ行列のタプルのベクターであり、例えば[("network1name",rand(Complex{Float64},2,2), ("network2name",rand(Complex{Float64},2,2)]のようになります。`connections`は、ネットワーク名とポートのタプルのベクターのベクターであり、例えば[[("network1name",1), ("network2name",2)]]のようになります。ここで、network1とnetwork2は接続される2つのネットワークであり、1と2は接続するポートを示す整数です。

この関数は、スプリッターを自動的に追加することにより、2つ以上のポート間の接続をサポートします。

# 例

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])];
connections = [[("S1",1),("S2",2)]];
JosephsonCircuits.connectS(networks,connections)

# 出力
(S = [[0.5 0.5; 0.5 0.5]], ports = [[("S1", 2), ("S2", 1)]])
```

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5],[("S3",5),("S3",6)])];
connections = [("S1","S3",1,6)];
JosephsonCircuits.connectS(networks,connections)

# 出力
(S = [[0.5 0.5; 0.5 0.5]], ports = [[("S1", 2), ("S3", 5)]])
```
