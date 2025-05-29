```
PDVec{K,V}(; kwargs...)
PDVec(iter; kwargs...)
PDVec(pairs...; kwargs...)
```

FCIQMCおよび[KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl)で使用するための辞書ベースのベクトルライクデータ構造です。主に`Dict`のように振る舞いますが、`norm`や`dot`などのさまざまな線形代数演算をサポートし、[VectorInterface](https://github.com/Jutho/VectorInterface.jl)で定義されたインターフェースを持っています。

`PDVec`のPは並列を意味します。`PDVec`は`mapreduce`、`foreach`、およびさまざまな線形代数演算をスレッド方式で実行します。MPIが利用可能な場合、これらの操作は自動的に分散されます。そのため、ベクトルの[`localpart`](@ref)で明示的に実行しない限り、`pairs`、`keys`、または`values`を直接反復処理することは推奨されません。

関連情報: [`AbstractDVec`](@ref)、[`DVec`](@ref)、[`InitiatorDVec`](@ref)。

## キーワード引数

  * `style =`[`default_style`](@ref)`(V)`: FCIQMCアルゴリズムでの生成戦略を選択するために使用される[`StochasticStyle`](@ref)。
  * `initiator =`[`NonInitiator`](@ref)`()`: FCIQMCで符号問題を解消するために使用される[`InitiatorRule`](@ref)。
  * `communicator`: MPIを使用する際の操作の実行方法を制御する[`Communicator`](@ref)。MPIを使用しない場合のデフォルトは[`NotDistributed`](@ref)、MPIを使用する場合のデフォルトは[`AllToAll`](@ref)。

# 拡張ヘルプ

## セグメンテーション

ベクトルは`Threads.nthreads()`個のサブ辞書に分割され、これをセグメントと呼びます。キーと値のペアがどの辞書にマッピングされるかは、キーのハッシュによって決まります。このセグメンテーションの目的は、並列処理を可能にすることです。`mapreduce`、`add!`、または`dot`（以下の完全なリスト）などの関数は、各サブ辞書を別々のスレッドで処理します。

関連情報: [`PDWorkingMemory`](@ref)。

### 例

```julia
julia> add = FermiFS2C((1,1,0,0), (0,0,1,1));

julia> op = HubbardMom1D(add; t=4/π^2, u=4);

julia> pv = PDVec(add => 1.0)
1-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↑↓↓⟩" => 1.0

julia> pv = op * pv
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => 1.0
  fs"|↑↑↓↓⟩" => 4.0
  fs"|↓↑↓↑⟩" => 1.0
  fs"|↓↑↑↓⟩" => -1.0
  fs"|⇅⋅⋅⇅⟩" => 1.0
  fs"|↑↓↓↑⟩" => -1.0
  fs"|⋅⇅⇅⋅⟩" => 1.0

julia> scale!(pv, -1); pv
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => -1.0
  fs"|↑↑↓↓⟩" => -4.0
  fs"|↓↑↓↑⟩" => -1.0
  fs"|↓↑↑↓⟩" => 1.0
  fs"|⇅⋅⋅⇅⟩" => -1.0
  fs"|↑↓↓↑⟩" => 1.0
  fs"|⋅⇅⇅⋅⟩" => -1.0

julia> dest = similar(pv)
0-element PDVec: style = IsDeterministic{Float64}()

julia> map!(x -> x + 2, dest, values(pv))
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => 1.0
  fs"|↑↑↓↓⟩" => -2.0
  fs"|↓↑↓↑⟩" => 1.0
  fs"|↓↑↑↓⟩" => 3.0
  fs"|⇅⋅⋅⇅⟩" => 1.0
  fs"|↑↓↓↑⟩" => 3.0
  fs"|⋅⇅⇅⋅⟩" => 1.0

julia> sum(values(pv))
-6.0

julia> dot(dest, pv)
10.0

julia> dot(dest, op, pv)
44.0
```

## MPI

MPIがアクティブな場合、すべての並列削減は`MPI.Allreduce!`の呼び出しで自動的にMPIランク間で削減されます。

分散設定では、`PDVec`は、ベクトルのローカルセグメントのみに対して反復処理を行うことを明示的に示さない限り、反復処理をサポートしません。これは[`localpart`](@ref)を使用して行います。一般的に、MPIを使用していない場合でも、明示的な反復が必要な場合は[`localpart`](@ref)を使用することが最良のプラクティスです。

## KrylovKitとの使用

`PDVec`は[KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl)の`eigsolve`と互換性があります。使用されると、対角化はスレッド方式で分散して行われます。この方法で複数のMPIランクを使用すると、メモリ負荷が効果的に分散されるわけではありませんが、著しいスピードアップが得られます。

### 例

```julia
julia> using KrylovKit

julia> add = BoseFS((0,0,5,0,0));

julia> op = HubbardMom1D(add; u=6.0);

julia> pv = PDVec(add => 1.0);

julia> results = eigsolve(op, pv, 4, :SR);

julia> results[1][1:4]
4-element Vector{Float64}:
 -3.4311156892322234
  1.1821748602612363
  3.7377753753082823
  6.996390417443125
```

## 並列機能

以下の関数はスレッド対応でMPI互換です：

  * Baseから: `mapreduce`およびその派生（`sum`、`prod`、`reduce`...）、`all`、`any`、`map!`（`values`のみに対して）、`+`、`-`、`*`
  * LinearAlgebraから: `rmul!`、`lmul!`、`mul!`、`axpy!`、`axpby!`、`dot`、`norm`、`normalize`、`normalize!`
  * [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl)で定義された完全なインターフェース

```
