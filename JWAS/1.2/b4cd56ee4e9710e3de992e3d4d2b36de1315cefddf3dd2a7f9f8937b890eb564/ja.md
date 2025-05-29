```
set_covariate(model::MME,variables::AbstractString...)
```

  * **variables**を共変量として設定します; **model**は関数`build_model()`の出力です。

```julia
# build_modelを実行した後、変数ageとyearを共変量として設定できます
set_covariate(model,"age","year")
# または
set_covariate(model,"age year")
```
