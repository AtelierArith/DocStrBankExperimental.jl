```
struct ImageSpaceSolver{A<:LowRankLDLTAlgorithm,S<:MacaulayNullspaceSolver}
    ldlt::A
    null::S
end
```

モーメント行列のイメージ空間を `ldlt` を使用して計算し、その後 `null` で解決します。
