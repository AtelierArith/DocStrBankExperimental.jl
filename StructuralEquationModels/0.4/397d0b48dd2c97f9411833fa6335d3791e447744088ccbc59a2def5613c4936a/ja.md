```
params!(out::AbstractVector, partable::ParameterTable,
              col::Symbol = :estimate)
```

`partable`の`col`列からパラメータ値を`out`ベクターに抽出します。

`out`ベクターは`nparams(partable)`の長さである必要があります。`out`ベクターの*i*-番目の要素には、`params_labels(partable)`の*i*-番目のパラメータの値が含まれます。

この関数は、`partable`内の同じパラメータの重複する出現を結合し、値が一致しない場合はエラーを発生させることに注意してください。
