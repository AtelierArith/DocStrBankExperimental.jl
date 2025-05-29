```julia
exportG2o(
    dfg;
    poseRegex,
    solvable,
    ignorePriors,
    filename,
    overwriteMapping,
    varIntLabel,
    solveKey
)

```

因子グラフをg2oファイル形式にエクスポートします。

注意:

  * この関数はガウス（すなわち、ノーマル/MvNormal）因子のみをサポートしており、`AliasingScalarSampler`因子モデルなどの他のケースでは予測不可能な魔法が使用されます。
