```
getSignalNames(instantiatedModel::Modia.InstantiatedModel;
               getVar=true, getPar=true, getMap=true)::Vector{String}
```

[`@instantiateModel`](@ref) の結果に存在するか、（評価された）パラメータである変数の文字列ベクターを返します。

  * getVar=true の場合、Var(..) 変数が含まれます。
  * getPar=true の場合、Par(..) 変数が含まれます。
  * getMap=true の場合、Map(..) 変数が含まれます。
