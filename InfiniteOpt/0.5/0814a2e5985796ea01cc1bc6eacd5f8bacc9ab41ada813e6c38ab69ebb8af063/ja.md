```
parameter_refs(data::AbstractMeasureData)::Union{GeneralVariableRef,
                                                 AbstractArray{GeneralVariableRef}}
```

`data`内の無限パラメータ参照を返します。これは、測定の追加に使用される内部関数として意図されています。ユーザー定義の測定データ型は、この関数を拡張する必要があります。さもなければ、エラーが発生します。
