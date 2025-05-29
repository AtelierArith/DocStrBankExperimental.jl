```
ClosedPath(c::AbstractVector; tol=<default>)
ClosedPath(P::Path; tol=<default>)
```

曲線のベクトル `c` または既存のパスを指定して、閉じたパスを構築します。パスはすべての頂点で連続性（許容誤差 `tol` に対して）をチェックされます。
