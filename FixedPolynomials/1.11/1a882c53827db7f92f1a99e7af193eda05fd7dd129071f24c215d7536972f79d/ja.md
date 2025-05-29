```
homogenize(p::Polynomial [, variable = :x0])
```

`p`を同次にします。`ishomogenized(p)`が`true`の場合、これは単に恒等式です。同次化変数は常に多項式の最初の変数として考慮されます。
