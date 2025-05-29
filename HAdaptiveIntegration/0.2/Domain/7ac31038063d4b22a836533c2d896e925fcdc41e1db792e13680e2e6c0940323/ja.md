```
struct Simplex{D,T,N} <: AbstractDomain{D,T}
```

`D`次元の単体で、要素型`T`の`N=D+1`の頂点を持ちます。

## フィールド:

  * `vertices::SVector{N,SVector{D,T}}`: 単体の頂点。

## 不変条件 (**構築時に** チェックしない):

  * `N = D+1`

## コンストラクタ:

  * `Simplex(vertices...)`
  * `Simplex{T}(vertices...)`
  * `Simplex(vertices::SVector{N,SVector{D,T}})`
