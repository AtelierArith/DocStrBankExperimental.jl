```
diff(S::Spline, [op::Derivative = Derivative(1)]) -> Spline
```

`op * S` と同じです。

スプライン `S` の N 次導関数を新しいスプラインとして返します。
