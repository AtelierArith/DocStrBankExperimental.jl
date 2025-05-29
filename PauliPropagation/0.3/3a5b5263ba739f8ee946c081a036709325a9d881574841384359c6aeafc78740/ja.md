```
overlapbyorthogonality(pstr::PauliString, orthogonalfunc::Function)
```

整数パウリ文字列を状態または演算子と重ね合わせる関数で、パウリ文字列が直交している場合は真を返し、したがって重なりが0になります。例として、`orthogonalfunc`は`containsXorY`で、パウリ文字列がXまたはYパウリを含む場合に真を返します。直交していない場合、重なりは1です。これは、安定器状態との重なりに特に便利です。
