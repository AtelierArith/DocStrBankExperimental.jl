```
estimate_h(rd::RefElemData, md::MeshData)
estimate_h(e, rd::RefElemData, md::MeshData) # e = 要素インデックス
```

メッシュサイズを最小サイズ*of*ドメイン * |J|/|Jf| を通じて推定します。ここで |J| = O(hᵈ) および |Jf| = O(hᵈ⁻¹) です。
