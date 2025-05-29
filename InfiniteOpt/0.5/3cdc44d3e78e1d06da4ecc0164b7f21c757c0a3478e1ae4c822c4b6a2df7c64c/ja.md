```
add_measure(model::InfiniteModel, meas::Measure,
            name::String = "measure")::GeneralVariableRef
```

`model`に測定値を追加し、対応する測定値の参照を返します。これは`JuMP.add_variable`と同様の方法で動作します。これは内部メソッドとして意図されています。
