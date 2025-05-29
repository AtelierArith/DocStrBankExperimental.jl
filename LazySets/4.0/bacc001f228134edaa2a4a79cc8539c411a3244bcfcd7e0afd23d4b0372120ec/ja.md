# 拡張ヘルプ

```
isuniversal(P::AbstractPolyhedron, [witness]::Bool=false)
```

### アルゴリズム

`P` がユニバーサルであるのは、制約がない場合です。

証拠は `isuniversal(H)` を使用して生成され、ここで `H` は `P` の最初の線形制約です。
