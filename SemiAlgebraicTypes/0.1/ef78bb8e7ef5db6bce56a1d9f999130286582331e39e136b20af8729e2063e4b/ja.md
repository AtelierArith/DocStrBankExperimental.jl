```
remove_doublon!(m::Mesh{Float64}, eps::Float64=1.e-3)
```

距離eps以内にある重複点を1つの点に置き換えます。

epsのデフォルト値は1.e-3です。

警告: 法線は考慮されていません。
