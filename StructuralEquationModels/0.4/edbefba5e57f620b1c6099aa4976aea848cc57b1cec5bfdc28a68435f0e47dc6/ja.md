```
params(x::ParameterTable, col::Symbol = :estimate)
```

`partable`の`col`列からパラメータ値を抽出します。

値のベクトルを返します。*i*-番目の要素は、`params_label(partable)`の*i*-番目のパラメータの値に対応します。

この関数は、`partable`内の同じパラメータの重複する出現を結合し、値が一致しない場合はエラーを発生させることに注意してください。
