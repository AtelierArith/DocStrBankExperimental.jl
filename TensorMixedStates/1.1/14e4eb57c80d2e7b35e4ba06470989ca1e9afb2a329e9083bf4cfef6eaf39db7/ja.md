```
expect(::State, obs)
```

与えられた状態における `obs` の期待値を計算します。

# 例

```
expect(state, X(1)*Y(2) + Y(1)*Z(3))
expect(state, [X(1)*Y(2), X(3), Z(1)*X(2)])
```
