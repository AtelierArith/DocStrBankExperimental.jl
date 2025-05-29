`itersolve(clauses; verbose::Integer=0, num_threads::Integer=Sys.CPU_THREADS)`

  * `verbose` - 冗長性
  * `num_threads` - 使用するCPUスレッドの数

最初の引数は節のベクターです。各節はリテラルのベクターであり、各リテラルは `Lit(T)`, `NotLit(T)`, `XorLit(T)` または `XNorLit(T)` でカプセル化されています。ここで `T` は任意の型です。XorLit と XNotLit の項を含む節はXOR節であり、満たされる節の数は、満たされるために NotLit と XNorLit の数と同じ奇数性を持たなければなりません。Lit と NotLit の項を含む節は通常の論理和の節です。

すべての解に対する反復可能なオブジェクトを返します。

```julia
julia> import CryptoMiniSat
julia> # コーヒーにクリーム、紅茶にミルク
julia> cnf = [[XorLit(:coffee),XorLit(:tea)],[NotLit(:coffee),Lit(:cream)],[NotLit(:tea),Lit(:milk)]];
julia> collect(CryptoMiniSat.itersolve(cnf))
4-element Vector{Any}:
 Dict{Symbol, Bool}(:cream => 0, :milk => 1, :tea => 1, :coffee => 0)
 Dict{Symbol, Bool}(:cream => 1, :milk => 1, :tea => 1, :coffee => 0)
 Dict{Symbol, Bool}(:cream => 1, :milk => 1, :tea => 0, :coffee => 1)
 Dict{Symbol, Bool}(:cream => 1, :milk => 0, :tea => 0, :coffee => 1)
```
