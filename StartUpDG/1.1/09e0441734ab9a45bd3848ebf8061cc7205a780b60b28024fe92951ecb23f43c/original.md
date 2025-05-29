```
estimate_h(rd::RefElemData, md::MeshData)
estimate_h(e, rd::RefElemData, md::MeshData) # e = element index
```

Estimates the mesh size via min size*of*domain * |J|/|Jf|, since |J| = O(hᵈ) and |Jf| = O(hᵈ⁻¹). 
