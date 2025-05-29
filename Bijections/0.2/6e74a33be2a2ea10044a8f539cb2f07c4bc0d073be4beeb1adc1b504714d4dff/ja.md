```
hasvalue(b::Bijection, y)
```

Bijection `b` の像に `y` が含まれているかをチェックします。これは逆写像 `b.finv` が `y` をキーとして持っているかをチェックすることと同等であり、したがって `haskey` と同じくらい速いはずです。
