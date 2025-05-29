```
CustomBoundary(; boundary_behaviors...)
```

すべての状態変数に対して数学的境界条件を明示的に指定する境界。境界条件はキーワード引数として指定でき、キーはフィールドの名前で、値は均質境界条件の場合は `:dirichlet` または `:neumann` のいずれか、または非ゼロ値を含む `Pair` で、例えば `:dirichlet => 1` のようになります。

# 例

```
CustomBoundary(vel1 = :dirichlet => 1, vel2 = :dirichlet, vel3 = :neumann)
```
