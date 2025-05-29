```
solve_puzzle(p::Puzzle) -> PuzzleSolution

solve_puzzle(
    p::Puzzle,
    auxQs::AuxPuzzleQuantities = eval_aux_quantities(p);
    optimizer = GLPK.Optimizer,
    solverAttributes = ("msg_lev" => GLPK.GLP_MSG_OFF,),
    verbosity::Int = 1
) -> PuzzleSolution
```

[`Puzzle`](@ref) `p`を解決し、対応する[`PuzzleSolution`](@ref)を構築します。

このパズルは、整数線形計画法（ILP）ソルバーを使用して、Khanによる[方法](https://doi.org/10.1109/TG.2020.3036687)に従って解決されます。成功した場合、1つの解を返します。デフォルトでは、自由に利用できるソルバーGLPKを使用します。`p`以外のすべての引数はオプションです。

パズルインスタンス`p`は、[`Puzzle`](@ref)コンストラクタまたは[`read_puzzle_from_cwc`](@ref)を使用して構築できます。引数`optimizer`と`solverAttributes`は、ILPソルバーの選択とJuMPで使用する設定を指定します。JuMPのコマンドで使用するために：

```
JuMP.optimizer_with_attributes(optimizer, solverAttributes...)
```

これらの入力を設定する詳細については、JuMPのドキュメントを参照してください。

デフォルトでは、JuMPの解決概要を報告します。これを抑制するには、`verbosity=0`を設定してください。
