```
PolynomialRatio(b, a)
```

フィルタ表現は、伝達関数の分子 `b` と分母 `a` の係数に基づいています：

$$
H(s) = \frac{\verb!b[1]! s^{m-1} + \ldots + \verb!b[m]!}{\verb!a[1]! s^{n-1} + \ldots + \verb!a[n]!}
$$

または同等に：

$$
H(z) = \frac{\verb!b[1]! + \ldots + \verb!b[n]! z^{-n+1}}{\verb!a[1]! + \ldots + \verb!a[n]! z^{-n+1}}
$$

`b` と `a` は、最高次から最低次に順序付けられた `Polynomial` オブジェクトまたはベクトルとして指定できます。
