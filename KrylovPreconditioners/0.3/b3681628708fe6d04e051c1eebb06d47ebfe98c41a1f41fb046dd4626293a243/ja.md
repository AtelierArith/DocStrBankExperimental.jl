```
function update!(p, J::SparseMatrixCSC)
```

CPU用のCSC形式のスパースヤコビ行列`J`から前処理器`p`を更新します。

これはGPU用と同じアルゴリズムを実装しており、ブロックの数が増えるとCPU上で非常に遅くなります。
