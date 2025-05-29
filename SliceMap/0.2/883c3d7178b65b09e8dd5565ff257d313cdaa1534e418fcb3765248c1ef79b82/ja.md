```
MapCols{d}(f, m::Matrix, args...)
```

`mapcols(f, m, args...)`に似ていますが、`m`を`SVector{d}`列にスライスします。長さ`d = size(M,1)`は理想的には型の安定性のために提供されるべきですが、必須ではありません。

TrackerとZygoteの勾配は、各スライスに対して`ForwardDiff`を使用します。
