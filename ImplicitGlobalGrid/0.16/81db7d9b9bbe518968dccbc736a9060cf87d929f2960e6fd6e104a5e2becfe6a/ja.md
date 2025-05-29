```
init_global_grid(nx, ny, nz)
me, dims, nprocs, coords, comm_cart = init_global_grid(nx, ny, nz; <keyword arguments>)
```

MPIプロセスの直交グリッドを初期化します（デフォルトでMPI自体も初期化します）し、暗黙的にグローバルグリッドを定義します。

# 引数

  * {`nx`|`ny`|`nz`}`::Integer`: 次元 {x|y|z} におけるローカルグリッドの要素数。
  * {`dimx`|`dimy`|`dimz`}`::Integer=0`: 次元 {x|y|z} におけるプロセスの希望数。デフォルトでは（値 `0`）、与えられた制約に基づいてプロセスのトポロジーができるだけコンパクトに作成されます。これは、システムにインストールされているMPI実装によって処理されます。詳細については、該当するドキュメントの `MPI_Dims_create` の仕様を参照してください。
  * {`periodx`|`periody`|`periodz`}`::Integer=0`: グリッドが次元 {x|y|z} において周期的であるか（`1`）そうでないか（`0`）。
  * `quiet::Bool=false`: グローバルグリッドのサイズなどの情報を印刷するかどうか（`true`）またはしないか（`false`）。

!!! note "高度なキーワード引数"
      * `overlaps::Tuple{Int,Int,Int}=(2,2,2)`: 次元 x, y, z において隣接するローカルグリッドが重なる要素数。デフォルト（値 `(2,2,2)`）では、プロセス 1 のサイズ (`nx`, `ny`, `nz`) の配列 `A` (`A_1`) は、隣接するプロセス 2 の配列 `A` (`A_2`) と `2` インデックスで重なります。例えば、`overlaps[1]=2` でプロセス 2 が次元 x におけるプロセス 1 の右隣の場合、`A_1[end-1:end,:,:]` は `A_2[1:2,:,:]` と重なります。つまり、`update_halo!(A)` を呼び出すたびに、`all(A_1[end-1:end,:,:] .== A_2[1:2,:,:])` になります（`A_1[end,:,:]` はプロセス 1 のハローで、`A_2[1,:,:]` はプロセス 2 のハローです）。y および z の次元についても同様です。
      * `halowidths::Tuple{Int,Int,Int}=max.(1,overlaps.÷2)`: 次元 x, y, z における配列のハローのデフォルト幅（1 より大きくなければなりません）。デフォルトは、関数 [`update_halo`](@ref) で配列ごとに上書きできます。
      * `disp::Integer=1`: 隣接プロセスを決定するための `MPI.Cart_shift` への変位引数。
      * `reorder::Integer=1`: 直交プロセスのトポロジーを作成するための `MPI.Cart_create` への再配置引数。
      * `comm::MPI.Comm=MPI.COMM_WORLD`: 直交プロセスのトポロジーを作成するための `MPI.Cart_create` への入力コミュニケーター引数。
      * `init_MPI::Bool=true`: MPI を初期化するかどうか（`true`）またはしないか（`false`）。
      * `device_type::String="auto"`: 利用可能な場合に使用されるデバイスタイプ：`"CUDA"`、`"AMDGPU"`、`"none"` または `"auto"`。GPUも持つシステムでCPUのみを使用したい場合は、`device_type="none"` に設定します。`device_type` が `"auto"`（デフォルト）の場合、使用されるデバイスプログラミングモジュール（CUDA.jl または AMDGPU.jl）が ImplicitGlobalGrid の前にインポートされたかに応じて自動的に決定されます。両方がインポートされている場合、`device_type` が `"auto"` に設定されているとエラーが発生します。
      * `select_device::Bool=true`: CUDA または AMDGPU がインポートされ、`device_type` が `"none"` でない場合にデバイス（GPU）を自動的に選択するかどうか（`true`）またはしないか（`false`）。`true` の場合、ノードローカルの MPI ランクに対応するデバイスを選択します。このデバイス選択方法は、単一および複数デバイスの計算ノードの両方に適しており、一般的に推奨されます。また、*関数* [`select_device`](@ref) のデフォルトのデバイス選択方法でもあります。

    詳細については、MPI.jl / MPI のドキュメントを参照してください。


# 戻り値

  * `me`: プロセスのMPIランク。
  * `dims`: 各次元のプロセス数。
  * `nprocs`: プロセスの数。
  * `coords`: プロセスの直交座標。
  * `comm_cart`: 作成された直交プロセスのトポロジーのMPIコミュニケーター。

# 一般的な使用例

```
init_global_grid(nx, ny, nz)                  # 基本的な呼び出し（オプションの入力および出力引数なし）。
me, = init_global_grid(nx, ny, nz)            # 'me' をキャプチャ（',' に注意！）。
me, dims = init_global_grid(nx, ny, nz)       # 'me' と 'dims' をキャプチャ。
init_global_grid(nx, ny, nz; dimx=2, dimy=2)  # MPIプロセスの直交グリッドの次元 x および y におけるプロセス数を 2 に固定します（プロセス数は次元 z でのみ変動可能）。
init_global_grid(nx, ny, nz; periodz=1)       # 次元 z における境界を周期的にします。
```

参照： [`finalize_global_grid`](@ref)、[`select_device`](@ref)
