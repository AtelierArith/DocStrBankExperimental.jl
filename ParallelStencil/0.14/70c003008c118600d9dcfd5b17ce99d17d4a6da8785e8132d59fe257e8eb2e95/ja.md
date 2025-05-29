```
@parallel kernel
@parallel inbounds=... memopt=... ndims=... kernel
```

`kernel`を並列に宣言し、`ParallelStencil.FiniteDifferences{1D|2D|3D}`のいずれかのサブモジュール（または互換性のあるカスタムモジュールまたはマクロのセット）を使用してステンシル計算を実行します。

# オプションのキーワード引数

  * `inbounds::Bool`: カーネルに`@inbounds`を適用するかどうか。デフォルトは`false`または[`@init_parallel_stencil`](@ref)の`inbounds`キーワード引数で設定された値です。
  * `memopt::Bool=false`: ステンシル特有の高度なオンチップメモリ最適化を実行するかどうか。`memopt=true`が設定されている場合、対応するカーネル呼び出しでも設定されている必要があります。

!!! note "高度なオプションのキーワード引数"
      * `ndims::Integer|Tuple`: カーネル内のステンシル計算に使用される次元の数：1、2、または3（または、与えられた値ごとにメソッドを生成するために前のいずれかを含むタプル - 使用されるマクロが選択された`ndims`の任意の値で動作する場合にのみ正しく機能します！）。デフォルトは[`@init_parallel_stencil`](@ref)の`ndims`キーワード引数で設定できます。キーワード引数`N`は、次元の数に基づいてディスパッチするために`ndims`がタプルである場合に必須になります（以下を参照）。
      * `N::Integer|Tuple`: カーネルメソッドシグネチャ内の型パラメータ`N`が取るべき値。値は通常、`@parallel`マクロまたは`@init_parallel_stencil`の対応するキーワード引数で設定された`ndims`に基づいて計算され、評価前に式に置き換えられます。これにより、カーネルメソッド内の次元の数に基づいてディスパッチが可能になります（例：`@parallel ndims=(1,3) N=ndims function f(A::Data.Array{N}) ... end`）。`ndims`がタプルである場合、キーワード引数`N`は必須であり、さらに`ndims`と同じ長さのタプルでなければなりません。


参照：[`@init_parallel_stencil`](@ref)

---

```
@parallel kernelcall
@parallel memopt=... kernelcall
@parallel ∇=... kernelcall
@parallel ∇=... memopt=... kernelcall
```

!!! note "高度な"
    ```
    @parallel ranges kernelcall
    @parallel nblocks nthreads kernelcall
    @parallel ranges nblocks nthreads kernelcall
    @parallel (...) memopt=... configcall=... backendkwargs... kernelcall
    @parallel ∇=... ad_mode=... ad_annotations=... (...) memopt=... backendkwargs... kernelcall
    ```


`kernelcall`を並列に宣言します。カーネルは、[`@init_parallel_kernel`](@ref)で選択された並列化のためにパッケージによって必要に応じて自動的に呼び出されます。呼び出しの最後で同期します（キーワード引数を介してストリームが指定されている場合、そのストリームのみが同期されます）。キーワード引数`∇`は、カーネル自体ではなく勾配カーネルへの並列呼び出しをトリガーします。自動微分は、Enzyme.jlパッケージを使用して実行されます（以下で使用されるEnzyme特有の用語については、対応するドキュメントを参照してください）；Enzymeは、対応する拡張を読み込むためにParallelStencilの前にインポートする必要があります。

# 引数

  * `kernelcall`: 並列に宣言されたカーネルへの呼び出し。

!!! note "高度なオプション引数"
      * `ranges::Tuple{UnitRange{},UnitRange{},UnitRange{}} | Tuple{UnitRange{},UnitRange{}} | Tuple{UnitRange{}} | UnitRange{}`: 計算を実行する必要がある各次元のインデックスの範囲。
      * `nblocks::Tuple{Integer,Integer,Integer}`: [`@init_parallel_kernel`](@ref)でCUDA、AMDGPU、またはMetalパッケージが選択された場合に使用されるブロックの数。
      * `nthreads::Tuple{Integer,Integer,Integer}`: [`@init_parallel_kernel`](@ref)でCUDA、AMDGPU、またはMetalパッケージが選択された場合に使用されるスレッドの数。


# キーワード引数

  * `memopt::Bool=false`: 起動されるカーネルが`memopt=true`で生成されたかどうか（つまり、カーネル宣言でキーワードが設定されたことを意味します）。

!!! note "高度な"
      * `∇`: カーネルが自動的に微分される変数と、結果を格納するための各変数の複製を`->`で区切って指定します。例：`∇=(A->Ā, B->B̄)`。このキーワードを設定すると、カーネル自体ではなく勾配カーネルへの並列呼び出しがトリガーされます。複製変数はデフォルトで`DuplicatedNoNeed`の注釈とともにEnzymeに渡されます。例：`DuplicatedNoNeed(A, Ā)`。この動作を変更するには、キーワード引数`ad_annotations`を使用します。
      * `ad_mode=Enzyme.Reverse`: 自動微分モード（詳細についてはEnzyme.jlのドキュメントを参照してください）。
      * `ad_annotations=()`: 自動微分のためのEnzyme変数注釈の形式`(<keyword>=<variable(s)>, <keyword>=<variable(s)>, ...)`で、`<variable(s)>`は単一の変数または変数のタプル（例：`ad_annotations=(Duplicated=B, Active=(a,b))`）です。現在サポートされている注釈は：(:Const, :Active, :Duplicated, :DuplicatedNoNeed)です。
      * `configcall=kernelcall`: 並列に宣言されたカーネルへの呼び出しで、カーネル起動パラメータを決定するために使用されます。このキーワードは、低レベルのサブモジュール[`AD`](@ref)を使用した一般的な自動微分に便利です。
      * `backendkwargs...`: CUDA、AMDGPU、またはMetalにさらに渡されるキーワード引数（ThreadsおよびPolyesterには無視されます）。


!!! note "パフォーマンスノート"
    カーネル起動パラメータは、オプションのカーネル引数で定義されていない場合、ヒューリスティックに基づいて自動的に定義されます。CUDAおよびAMDGPUの場合、`nthreads`は通常(32,8,1)に設定され、`nblocks`はそれに応じて設定され、十分なスレッドが起動されることを保証します。


参照：[`@init_parallel_kernel`](@ref)
