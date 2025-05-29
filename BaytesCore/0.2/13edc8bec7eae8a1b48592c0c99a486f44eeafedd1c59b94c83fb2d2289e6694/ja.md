```julia
abstract type AbstractKernel
```

アルゴリズムカーネルのための抽象スーパタイプ。新しいカーネルは、対応する `AbstractAlgorithm` の内部に存在する必要があります。
