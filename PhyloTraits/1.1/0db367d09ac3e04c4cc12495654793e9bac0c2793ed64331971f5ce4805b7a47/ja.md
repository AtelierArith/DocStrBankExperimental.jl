```
ReconstructedStates
```

観察されたティップ値に基づいて推測された祖先状態の法則に関する情報を含む型。欠落しているティップは祖先状態と見なされます。

再構築された状態と予測区間は関数 `predict` を使用して回復でき、標準誤差は `stderror` で取得できます。

`ReconstructedStates` オブジェクトには、`traits_nodes`、`variances_nodes`、`nodenumbers`、`traits_tips`、`tipnumbers`、`model` のフィールドがあります。特定のフィールドに関するヘルプを得るには、"?ReconstructedStates.field" と入力してください。
