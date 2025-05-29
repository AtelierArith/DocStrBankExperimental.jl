```julia
buildGraphChain!(; ...)
buildGraphChain!(fctData; ...)
buildGraphChain!(fctData, fctType; ...)
buildGraphChain!(
    fctData,
    fctType,
    preFct_args_cb;
    stopAfter,
    varType,
    solverParams,
    solvable,
    fctKwargs,
    varTags,
    fctTags,
    postpose_cb,
    doRef,
    dfg,
    inflation_fct,
    varRegex,
    varLast,
    varCount,
    varPrefix
)

```

バイナリファクターを持つ変数のチェーンを構築します。

ノート：

  * `fctData[1]` は最初の変数（デフォルトの空の `dfg` に対しておそらく `:x0`）と整列し、

      * `:x0` には前の変数/ファクターデータがありません。

開発ノート

  * TODO [`IIF._buildGraphByFactorAndTypes!`](@ref) と統合し、RoME にラップしますか？
