```
AbstractQuasiNewtonDirectionUpdate
```

現在の [`QuasiNewtonState`](@ref) に基づいて次の方向を決定するための準ニュートン更新ルールの抽象表現です。

すべてのサブタイプはファンクタであるべきで、`H(M,x,d)` として呼び出すことができ、新しい方向の更新を計算します。
