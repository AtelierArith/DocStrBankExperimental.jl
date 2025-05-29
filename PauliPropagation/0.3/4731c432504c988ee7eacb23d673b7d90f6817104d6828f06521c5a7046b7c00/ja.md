```
overlapbyorthogonality(psum::PauliSum, orthogonalfunc::Function)
```

`PauliSum`を状態または演算子と重ね合わせる関数で、パウリ文字列が直交している場合はtrueを返し、したがって寄与しない。例として`orthogonalfunc`は`containsXorY`で、パウリ文字列がXまたはYパウリを含む場合にtrueを返す。直交していない場合、パウリ文字列はその係数で寄与する。これは特に安定器状態との重なりに役立ちます。
