```
abstract type EigSolver
```

この型から継承される構造体は、`mslp`、`sgiter`、`polyeig`などの特定のメソッドで発生する線形固有値問題を解くことができます。

`EigSolver`オブジェクトはNEPアルゴリズムに型として渡され、正しいバージョンの関数[`eig_solve`](@ref)をディスパッチするために使用されます。

# 例

最も一般的な使用ケースは、特に何も指定したくない場合です。なぜなら、[`DefaultEigSolver`](@ref)は、問題に応じて密な方法または疎な方法を使用するからです。しかし、この例では、`mslp`に疎ソルバーを使用させる方法を示します。

```julia-repl
julia> nep=nep_gallery("qdep0");
julia> λ,v = mslp(nep, eigsolvertype=ArnoldiEigSolver);
julia> norm(compute_Mlincomb(nep,λ,v))
9.323110647141726e-16
```

# 例

`EigSolver`は拡張性のために構築されています。例として、この例では問題を標準の線形固有問題にキャストし、それを解決するために組み込み関数を呼び出す単純な`EigSolver`を作成します。

型とクリエイターを作成します。

```julia-repl
julia> struct MyEigSolver <: EigSolver
   A
   E
   function MyEigSolver(A,E)
      return new(A,E)
   end
end

julia> import NonlinearEigenproblems.LinSolvers.eig_solve;
julia> function eig_solve(solver::MyEigSolver;nev = 1, target = 0)
   M = solver.E \ solver.A
   eig = eigen(M)
   i = argmin(abs.(eig.values))
   return eig.values[i], eig.vectors[:,i]
end
julia> nep=nep_gallery("dep0", 50);
julia> λ,v = mslp(nep, eigsolvertype=MyEigSolver, tol=1e-5);
julia> norm(compute_Mlincomb(nep,λ,v))
3.0777795031319117e-10
```

参照: [`eig_solve`](@ref), [`DefaultEigSolver`](@ref), [`EigenEigSolver`](@ref), [`ArnoldiEigSolver`](@ref), [`eig_solve`](@ref)
