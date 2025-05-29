```
DijkstraState(::DijkstraState{T, U}, src) where {T, U} -> DijkstraState{T, U}
```

DijkstraStateをクリーンアップして、メモリを再利用し、再割り当てを避ける。
