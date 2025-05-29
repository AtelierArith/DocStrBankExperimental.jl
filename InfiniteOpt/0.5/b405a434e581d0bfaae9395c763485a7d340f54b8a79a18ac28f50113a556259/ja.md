```
set_derivative_method(pref::IndependentParameterRef, 
                      method::AbstractDerivativeMethod)::Nothing
```

`pref`に関して取られる導関数の評価方法`method`を指定します。以前の方法に専属の内部サポートはすべて削除されます。また、手動で評価された導関数があれば、関連する導関数評価制約も削除されます。新しい導関数方法が既存の測定と互換性のないサポートを生成する場合はエラーが発生します。

**例**

```julia-repl
julia> set_derivative_method(d, OrthogonalCollocation(2))

```
