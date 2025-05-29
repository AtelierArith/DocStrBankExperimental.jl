```
relu(x::Complex)
```

複素数に対するReLU関数の拡張であり、Virtue et al. (2017)の「Better than Real: Complex-valued Neural Nets for MRI Fingerprinting」で導入された複素数の心臓形に基づいています。この関数は、xが実数である場合（したがってangle(x)=0またはangle(x)=π）にreluと同等です。
