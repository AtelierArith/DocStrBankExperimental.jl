```
off(obsfunc::ObserverFunction)
```

リスナー関数 `obsfunc.f` を `obsfunc.observable` のリスナーから削除します。`obsfunc` がスコープ外になると、これにより `obsfunc.f` とそれが閉じ込めた可能性のあるすべての値がガーベジコレクションされることができます（他に参照がない限り）。
