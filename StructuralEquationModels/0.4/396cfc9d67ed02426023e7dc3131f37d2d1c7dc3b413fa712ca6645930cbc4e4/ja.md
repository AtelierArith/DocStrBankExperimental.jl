```
sort_vars!(partable::ParameterTable)
sort_vars!(partables::EnsembleParameterTable)
```

`partable`内の変数をソートして、すべての独立変数が従属変数の前に来るようにし、それを`partable.sorted_vars`に格納します。

変数間の関係が非循環的であれば、ソートにより得られる*RAM*モデルの`A`行列は下三角行列になり、計算が速くなります。
