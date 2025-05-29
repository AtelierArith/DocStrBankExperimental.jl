```
mul!(A::ITensor, x::Number, B::ITensor)
```

ITensor Bをxでスカラー乗算し、その結果をAに格納します。`A .= x .* B`のように。
