```
listcustommacs(cxr::CharXRay)
```

`cxr`のさまざまな要素に対して利用可能なカスタムMACのリストを生成しました。

```
listcustommacs(elms::Set{Element}|AbstractVector{Element}|Element...|Material)
```

これらの要素によって生成および吸収される元素とX線の両方に対して利用可能なカスタムMACのリストを生成します。
