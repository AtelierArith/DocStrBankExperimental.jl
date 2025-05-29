```
Initialize_Gaugefields(NC,NDW,NN...;
    condition = "cold",mpi = false,PEs=nothing,mpiinit = nothing,verbose_level = 2,randomnumber="Random")
```

ゲージフィールドを初期化します。2Dまたは4Dがサポートされています。

### 例

4次元でランダムに分布したゲージフィールド（いわゆる「ホットスタート」）を持ちたい場合は、次のようにします：

```julia
U = Initialize_Gaugefields(NC,Nwing,NX,NY,NZ,NT,condition = "hot")
```

4次元で均一なゲージフィールド（いわゆる「コールドスタート」）を持ちたい場合は、次のようにします：

```julia
U = Initialize_Gaugefields(NC,Nwing,NX,NY,NZ,NT,condition = "cold")
```

### 戻り値：

  * `U`: Dim次元のベクトル。ここで、Dimは次元（Dim = 2または4）です。

### キーワード引数：

  * `condition`: `cold`（コールドスタート）または`hot`（ホットスタート）。デフォルトは`cold`です。
  * `mpi`: MPIを使用するかどうか。デフォルトは`false`です。MPIを使用したい場合は、`using MPI`を呼び出す必要があります。
  * `PEs`: `mpi = true`の場合、`PEs = [2,2,2,2]`を設定する必要があります。これはMPIプロセスの領域の数です。`prod(PEs)`は総MPIプロセスの数である必要があります。

### MPI

MPIを使用したゲージフィールドは十分にテストされていません。
