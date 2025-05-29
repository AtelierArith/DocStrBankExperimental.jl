```
NgonFace{N, T}
```

N個の頂点を接続する平面の面。省略形には以下が含まれます：

  * `LineFace{T} = NgonFace{2,T}`
  * `TriangleFace{T} = NgonFace{3,T}`
  * `QuadFace{T} = NgonFace{4,T}`
  * `GLTriangleFace = TriangleFace{GLIndex}`
