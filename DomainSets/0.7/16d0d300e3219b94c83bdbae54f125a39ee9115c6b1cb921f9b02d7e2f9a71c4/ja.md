```
Ball{T,C} <: Domain{T}
```

要素の体積に対する抽象スーパタイプで、`norm(x-center(ball)) < radius(ball)`（開球）または`norm(x-center(ball)) <= radius(ball)`（閉球）を満たすもの。
