```
fillopacity(value)
```

塗りつぶしの不透明度を定義します。ここで、0≤value≤1です。svgの場合、ネストされたコンテキストは親コンテキストから継承されます。例えば、`(context(), fillopacity(a), (context(), fill(c::String), circle()))`のようになります。
