```
root_of_unity_as_args(a::QQBarFieldElem)
```

与えられた `a` が $e^{2 \pi i p / q}$ に等しい整数のペア `(q, p)` を返します。分母 `q` は最小であり、$0 \le p < q$ です。`a` が単位根でない場合は例外をスローします。
