```
@CellType(name, <キーワード引数>)
```

セルタイプを作成します。これにより、キーワード引数 `celltype` を使用して `@zeros`、`@ones`、`@rand`、`@falses`、`@trues` または `@fill` に渡すことができます。

!!! note "高度な情報"
    要素タイプ `eltype` は、[`@init_parallel_stencil`](@ref) で選択されたデフォルトの `numbertype` の代わりに使用するために、キーワード引数として明示的に渡すことができます。デフォルトの `numbertype` が選択されていない場合は、[`@init_parallel_stencil`](@ref) で、キーワード引数 `eltype` は必須です。ただし、`parametric=true` が設定されている場合は除きます。これは、パフォーマンスに重要な計算でデータ型の変換が発生しないように注意して使用する必要があります。


# 引数

  * `name`: セルタイプの名前。

# キーワード引数

  * `eltype::DataType`: 要素のタイプ。数値、インデックス、ブール値、または列挙型を指定できます。
  * `fieldnames::String|NTuple{N,String}`: セルのフィールドの名前。フィールド名が定義されている場合でも、セルの値には常に配列インデックスでアクセスできます。
  * `dims::Integer|NTuple{N,Integer}=length(fieldnames)`: セルの次元。セルは単一の値または指定された次元のN次元配列を含むことができます。有効な `dims` 引数は `prod(dims)==length(fieldnames)` を満たす必要があります。`dims` が省略された場合、自動的に `dims=length(fieldnames)` に設定され、適切な長さの1次元配列を含むセルが定義されます。

!!! note "高度な情報"
      * `parametric::Bool=false`: セルタイプが固定またはパラメトリックな要素タイプを持つかどうか。`parametric=true` が設定されている場合、キーワード引数 `eltype` は無効です。


# 例

```
@CellType SymmetricTensor2D fieldnames=(xx, zz, xz)
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D)

@CellType SymmetricTensor3D fieldnames=(xx, yy, zz, yz, xz, xy)
#(...)
A = @zeros(nx, ny, nz, celltype=SymmetricTensor3D)

@CellType Tensor2D fieldnames=(xxxx, yxxx, xyxx, yyxx, xxyx, yxyx, xyyx, yyyx, xxxy, yxxy, xyxy, yyxy, xxyy, yxyy, xyyy, yyyy) dims=(2,2,2,2)
#(...)
A = @zeros(nx, ny, celltype=Tensor2D)

@CellType SymmetricTensor2D fieldnames=(xx, zz, xz) parametric=true
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D{Float32})

@CellType SymmetricTensor2D fieldnames=(xx, zz, xz) eltype=Float32
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D)
```

参照: [`@zeros`](@ref)、[`@ones`](@ref)、[`@rand`](@ref)、[`@falses`](@ref)、[`@trues`](@ref)、[`@fill`](@ref)
