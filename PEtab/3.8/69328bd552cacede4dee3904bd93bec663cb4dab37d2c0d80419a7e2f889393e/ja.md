```
get_x(prob::PEtabODEProblem; linear_scale = false)::ComponentArray
```

`prob`によって期待される正しい順序のパラメータを持つ名目パラメータベクトルを取得します。名目値は、`PEtabParameter`を作成する際や、問題がPEtab標準形式で提供される場合にパラメータテーブルで指定できます。

操作を容易にするため（例：値の変更）、パラメータベクトルは`ComponentArray`として返されます。`ComponentArray`との対話方法については、ドキュメントおよびComponentArrays.jlの[ドキュメント](https://github.com/jonniedie/ComponentArrays.jl)を参照してください。

[`PEtabParameter`](@ref)も参照してください。

## キーワード引数

  * `linear_scale`: パラメータを線形スケールで返すかどうか。デフォルトでは、パラメータは推定されるスケールで返され、デフォルトでは`log10`であり、これがパラメータ推定のパフォーマンスを向上させることがよくあります。
