```
reconcile!(path::Path, endpoint::Point, end_direction, rule::RouteRule, waypoints, waydirs;
    initialize_waydirs = false)
```

`path`が`endpoint`に`end_direction`でルーティングできることを`rule, waypoints, waydirs`を使用して確認するか、エラーをスローします。

一般的な`RouteRule`に対しては何もしません。`RouteRule`のサブタイプは、`route!`が呼び出されたときに独自の検証を行うための特化したメソッドを実装することがあります。

`waypoints`と`waydirs`に推測された制約を挿入して、パスを脚ごとに描画できるようにする場合があります。たとえば、`rule::StraightAnd90`、ウェイポイントなし、`α1(path) == end_direction`の`reconcile!`は、`p1(path)`と`endpoint`の間の中間地点にウェイポイントを挿入し、反対の曲がりを持つ2つの連続した`StraightAnd90`の脚を可能にします。
