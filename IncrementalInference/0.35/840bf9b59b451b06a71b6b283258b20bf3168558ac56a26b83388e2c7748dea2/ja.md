```julia
makeSolverData!(dfg; solvable, varList, solveKey)

```

`varList`の変数についてチェックし、必要に応じて両方の`：default`および`：parametric`のsolveKeyのためにsolverDataオブジェクトを作成します。

例

```julia
num_made = makeSolverData(fg; solveKey=:parametric)
```

ノート

  * JuliaRobotics/IncrementalInference.jlの問題1637の解決の一部

DevNotes

  * TODO、parametric solvesは常にsolveKey `:parametric`にあると仮定しています。

参照: [`doautoinit!`](@ref), [`initAll!`](@ref)
