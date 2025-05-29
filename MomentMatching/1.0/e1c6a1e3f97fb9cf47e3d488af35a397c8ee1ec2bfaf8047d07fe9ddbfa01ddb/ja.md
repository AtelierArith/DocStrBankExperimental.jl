```julia
mergegloloc(
    estset::MomentMatching.EstimationSetup,
    resultglo::MomentMatching.EstimationResult,
    resultloc::MomentMatching.EstimationResult;
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult

```

グローバルおよびローカル推定の結果をマージします。入力が順序付けられていることを前提とし、ローカルから aux, presh, pmm を使用します。
