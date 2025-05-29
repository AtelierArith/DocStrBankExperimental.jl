```
@init_parallel_stencil(package, numbertype, ndims)
@init_parallel_stencil(package, numbertype, ndims, inbounds=...)
@init_parallel_stencil(package=..., ndims=..., inbounds=...)
```

パッケージParallelStencilを初期化し、その主な機能にアクセスします。`@init_parallel_stencil`が呼び出されたモジュール内に`Data`というモジュールを作成します。モジュール`Data`には、`Data.Number`、`Data.Array`、および`Data.CellArray`という型が含まれています（`@init_parallel_stencil`を呼び出した後に`?Data`を実行してモジュールの完全な説明を確認してください）。

# 引数

  * `package::Module`: 並列化に使用されるパッケージ（GPU用のCUDA、AMDGPU、またはMetal、またはCPU用のThreadsまたはPolyester）。
  * `numbertype::DataType`: @zeros、@ones、@rand、@fillおよびモジュール`Data`のすべての配列型で使用される数値の型（例：Float32またはFloat64）。`@init*parallel*stencil`の後に`Data.Number`に含まれます。`numbertype`は、他の引数がキーワード引数として与えられる場合は省略可能です（その場合、モジュール`Data`が提供する型を使用する際には`numbertype`を明示的に指定する必要があります）。
  * `ndims::Integer`: カーネル内のステンシル計算に使用される次元数：1、2、または3（各カーネル定義で上書き可能）。
  * `inbounds::Bool=false`: デフォルトでカーネルに`@inbounds`を適用するかどうか（各カーネル定義で上書き可能）。

参照：[`Data`](@ref)
