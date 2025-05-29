`solve(clauses; verbose::Integer=0, num_threads::Int = Sys.CPU_THREADS)`

  * `verbose` - 冗長性
  * `num_threads` - 使用するCPUスレッドの数

問題が充足可能であれば、解を返します。充足可能な解は辞書として表現されます。

最初の引数は節のベクターです。各節はリテラルのベクターであり、各リテラルは `Lit(T)`, `NotLit(T)`, `XorLit(T)` または `XNorLit(T)` でカプセル化されています。ここで `T` は任意の型です。XorLit と XNotLit の項を含む節はXOR節であり、満たされる節の数は、満たされるために NotLit と XNorLit の数と同じパリティでなければなりません。Lit と NotLit の項を含む節は通常の選言節です。

問題が充足不可能な場合、メソッドは `:unsatisfiable` シンボルを返します。

```julia
julia> import CryptoMiniSat
julia> # コーヒーにクリーム、紅茶にミルク
julia> cnf = [[XorLit(:coffee),XorLit(:tea)],[NotLit(:coffee),Lit(:cream)],[NotLit(:tea),Lit(:milk)]];
julia> CryptoMiniSat.solve(cnf)
Dict{Symbol, Bool} with 3 entries:
  :cream  => 0
  :milk   => 1
  :tea    => 1
  :coffee => 0
```
