```
ishermitian(T::ITensor; kwargs...)
```

ITensorがエルミート演算子であるかどうかをテストします。つまり、ITensorの`dag`を取り、そのインデックスを転置することが数値的に同じITensorを返すかどうかを確認します。
