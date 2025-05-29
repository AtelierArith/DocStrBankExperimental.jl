```
point(P::AbstractPath, t::Real)
P(t)
```

パラメータ値 `t` に沿ったパス `P` の点を計算します。`[k,k+1]` の範囲の `t` の値は、パスの曲線 k に沿った `[0,1]` の値に対応します。ここで、k = 1,2,...,length(P)-1 です。

```
point(P::AbstractPath, t::AbstractVector)
```

パス `P` のために `point` メソッドをベクトル化します。
